# Unit of Work

* EF is already UoW/Repo pattern
* Entity Framework, not Entity Library
    * We commit on using a framework. If we build wrappers around it, we lose a lot of it's benefit.
    * Have you ever switch the ORM?
* The core argument for using repositories is to prevent leaking EF dependent code into your domain. That argument is not wrong, it just comes with a steep cost, i.e. a high-complexity uow/repo layer, which is now being regarded (by some, at least) as too high a price to pay for what it gives back.
* uow/repo are an anti-pattern to Entity Framework.
* uow/repo usually produces a lot of boilerplate and problems even though EF already solved those


Get rid of repo / uow boilderplate
```cs
// OLD
using (var uow = new UnitOfWork())
{
    uow.FooRepository.Add(myFoo);
    uow.BarRepository.Update(myBar);
    uow.BazRepository.Delete(myBaz);
   
    uow.Commit();
}
```

```cs
// NEW
using (var db = new MyContext())
{
    db.Foos.Add(myFoo);
    db.Bars.Update(myBar);
    db.Bazs.Delete(myBaz);

    db.SaveChanges();
}
```

