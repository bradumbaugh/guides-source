### Modifying Attributes

Once a record has been loaded, you can begin making changes to its
attributes. Attributes behave just like normal properties in Ember.js
objects. Making changes is as simple as setting the attribute you
want to change:

```javascript
var tyrion = this.store.findRecord('person', 1);
// ...after the record has loaded
tyrion.set('firstName', "Yollo");
```

All of the Ember.js conveniences are available for
modifying attributes. For example, you can use `Ember.Object`'s
`incrementProperty` helper:

```javascript
person.incrementProperty('age'); // Happy birthday!
```

You can tell if a record has outstanding changes that have not yet been
saved by checking its `isDirty` property. You can also see what parts of
the record were changed and what the original value was using the
`changedAttributes` function.  `changedAttributes` returns an object,
whose keys are the changed properties and values are an array of values
`[oldValue, newValue]`.

```javascript
person.get('isAdmin');      //=> false
person.get('isDirty');      //=> false
person.set('isAdmin', true);
person.get('isDirty');      //=> true
person.changedAttributes(); //=> { isAdmin: [false, true] }
```

At this point, you can either persist your changes via `save()` or you
can rollback your changes. Calling `rollback()` reverts all the
`changedAttributes` to their original value.

```javascript
person.get('isDirty');      //=> true
person.changedAttributes(); //=> { isAdmin: [false, true] }

person.rollback();

person.get('isDirty');      //=> false
person.get('isAdmin');      //=> false
person.changedAttributes(); //=> {}
```

<!-- eof - needed for pages that end in a code block  -->
