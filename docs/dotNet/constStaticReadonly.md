# Const vs Static vs Readonly
Here's what you need to know about using <code>const</code>, <code>static</code>, and <code>readonly</code>:

1.	If you know the value will never, ever, ever change for any reason, use <code>const</code>. (Other Assemblies that use this value need to be recompiled before they get the new value)
2.	If you're unsure of whether or not the value will change, but you don't want other classes or code to be able to change it, use <code>readonly</code>.
3.	If you need a field to be a property of a type, and not a property of an instance of that type, use <code>static</code>.
4.	A <code>const</code> value is also implicitly <code>static</code>.
