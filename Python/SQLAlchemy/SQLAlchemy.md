
`where`, `filter` - одне і те ж саме, поля вказуються через імя моделі, та рівність череез `==`
`filter_by` - поля, вказуються як іменовані аргументи



`session.get` - повертає обєкт або `None`
`session.get_one` - повертає обєкт або викликає `NoResultFound`


Різниця роботи із обєктами та виразами:
```python
# objects: will execute 2 queies: get object and update them
instance = await session.get(User, id)
instance.name = "New name"
sessioin.commit()

# expresoins: will perform the same, but in one query
stmt = update(User).filter_by(id=id).values(name="New name")
await session.execute(stmt)
await sessoin.commit()
```


`session.expire(<Model>)` - відміняє всі зміни моделі **які зараз в сесії** (які не були збережені з допомогою `commit`)

### relationship
`primaryjoin` - визначає, яким чином підвантажувати звязані моделі. З його допомогою можна контролювати як підгружаються звязані поля, або створювати додаткові атрибути із специфічною вибіркою звязаних полів.
```python
class User(Base):
  id: Mapped[int] = mapped_column(primary_key=True)

  comments: Mapped[list[Comment]] = relationship(
    back_populates="user",
	primaryjoin="User.id == Comment.user_id",  # default generated primary join
  )

  best_comments: Mapped[list[Comment]] = relationshp(
    back_populates="user",
    # get comments by specific condiition
    primaryjoin="and_(User.id == Comment.user_id, Comment.likes > 10)", 
  )
```


![[Виконання запитів]]

![[Методи flush та refresh]]

![[Завантаження звязаних моделей]]