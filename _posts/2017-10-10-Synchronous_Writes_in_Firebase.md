---
layout: post
unique_id: firebase_synchronous_writes
title: Synchronous Writes in Firebase
categories: [technical]
locations: 
---

This post is focused on the [Firebase Admin Java API](https://github.com/firebase/firebase-admin-java) which we use to build services to support our app.

[Firebase Realtime Database](https://firebase.google.com/) is a lovely key-value tree-structured database.  To write a value in Firebase, you can simply do:

```
FirebaseDatabase database = FirebaseDatabase.getInstance();
DatabaseReference ref = database.getReference("example");
ref.write("Hello World");
```

The entire database is a tree, so here we store "Hello World" into the "example" child of the root.

A few obvious questions:
* does that write block until it succeeds?
* what if the database write fails?

This `write` method does NOT block.  It is handled asynchronously on a separate thread.

Aside from encouraging developers to ignore failed writes, this has a few other issues:
* what if I want to set a timeout on writes?
* what if I want to write to ref1 and then write to ref2 upon success?
* what if I want to record how long it takes to do my writes?

Luckily, the crafty API developers provide the ability to add an optional `CompletionListener` argument (there's also a Task object if you do not provide the argument, which they intend to deprecate in favor of `com.google.api.core.ApiFuture`).

If you want a synchronous write which properly throws on error, you can use a latch and a reference:

```
public void synchronousWrite(DatabaseReference ref, Object value) {
    CountDownLatch latch = new CountDownLatch(1);
    AtomicReference<DatabaseError> error = new AtomicReference<>();
    ref.write(
        value,
        (error, ref2) => {
    	    error.set(databaseError);
            latch.countDown();
        }
    );

    latch.await(TIMEOUT_DURATION, TimeUnit.SECONDS);

    if (error.get() != null) {
        throw IllegalStateException("sadness", error.get().toException());
    }
}
```

There are some gotchas if you aren't careful though.  See [this post]({{ site.baseurl }}/Subscribers_Synchronous_Writes_in_Firebase).

I actually wrapped Firebase behind a module which wraps the `read`, `update`, and `delete` properly as well.  Leave a message if you're interested in the wrapper library and I can upload to GitHub :P
