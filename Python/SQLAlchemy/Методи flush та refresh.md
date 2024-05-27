`flush` використовується для генерації первинних ключів (або інших полів) без збереження, `refresh` для оновлення обєкту до актуальної версії:
```python
# simple commit
user = User(name="andrii", username="andrymyzik")
session.add(user)
user.id  # raise error, since object is not yet recorded to db
session.commit()
session.refresh(user)  # refresh instance
user.id  # some id can be accessed


# flush usage
user = User(name="galynka", username="galko")
session.add(user)
session.flush()
user.id  # primary key can be accessed, but user instance not saved to db yet
session.commit()  # save user to db
```