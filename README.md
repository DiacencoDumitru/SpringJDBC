### `Что такое Statement?`

Объект Statement в Java используется для выполнения SQL-запросов, таких как SELECT, INSERT, UPDATE, и DELETE, к базе
данных. Он является частью пакета java.sql.

```java 
ResultSet resultSet = statement.executeQuery("SELECT * FROM Person");
```

### `Что такое PreparedStatement?`
PreparedStatement — это специальный объект в Java для выполнения SQL-запросов к базе данных, который:
1. Делает запросы безопасными.
2. Упрощает работу с параметрами.
3. Повышает производительность.
   Преимущества PreparedStatement 
4. **Защита от SQL-инъекций.** SQL-инъекция — это, когда злоумышленник вводит вредоносный SQL-код через пользовательский ввод.
```java
String SQL = "INSERT INTO Person(name, age) VALUES (?, ?)";
PreparedStatement pstmt = connection.prepareStatement(SQL);
pstmt.setString(1, userInputName);
pstmt.setInt(2, userInputAge);
pstmt.executeUpdate();
```
### `Что такое Рефлексия?`

Рефлексия (Reflection) — это механизм в Java, который позволяет программе во время выполнения:
Узнавать информацию о классах, методах, полях и конструкторах.
Вызывать методы и создавать объекты динамически.

```java
Class<?> clazz = Person.class; // Получить объект Class для класса Person
System.out.println("Имя класса: "+clazz.getName());
```

### Проект:

* Реализуем метод index() который будет возвращать всех людей из БД и возвращать их в наше представление
* Реализуем метод save() с помощью которого мы будем записывать нового человека в нашу БД
* Внедряем JDBC Driver (с помощью которого будем общаться с нашей БД)

### Дополнительно:

* PersonDAO: Данные для подключения к БД надо хранить отдельно (в дальнейшем эти данные вынесем отдельно)
* PersonDAO: Здесь мы с помощью рефлексии подгружаем класс `org.postgresql.Driver` и мы удастоверяемся в том что у нас
  этот класс загружен в оперативную память (использовать `static блок `)
* PersonDAO: Теперь когда у нас есть Driver для работы с БД, в наш `Connection` мы помещаем то что вернёт
  DriverManager.getConnection(URL, USERNAME, PASSWORD) наши компоненты переменных для подключения к БД
