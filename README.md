# Домашнее задание к занятию «2.5. Espresso»

Любые вопросы по решению задач задавайте в чате учебной группы.

---

## Задание 1. Реализация теста на проверку главного экрана

### Шаг 1. Запустите тестовый проект в Android Studio

1. Создайте новый репозиторий. Ссылку на него нужно будет прислать в качестве результата выполнения домашнего задания.
2. Выгрузите [тестовый проект](https://github.com/netology-code/mqa-homeworks/tree/main/2.5%20Espresso/simpleAppForEspresso).
3. Запустите тестовый проект в Android Studio.

### Шаг 2. Добавление зависимостей

1. Откройте файл /app/build.gradle.
2. Проверьте наличие и при необходимости добавьте зависимости в блок «dependencies»:
```java
     testImplementation 'junit:junit:4.13.2' 
     androidTestImplementation 'androidx.test.ext:junit:1.1.3' 
     androidTestImplementation 'androidx.test:rules:1.4.0'  
     androidTestImplementation 'androidx.test:runner:1.4.0' 
     androidTestImplementation 'androidx.test.espresso:espresso-core:3.4.0' 
```

### Шаг 3. Создание и настройка класса тестов

1. Создайте новый класс в директории /app/src/androidTest/java/ru/kkuzmichev/simpleappforespresso/.
2. Добавьте @RunWith(AndroidJUnit4.class) над именем класса.
3. Задайте правило для MainActivity внутри класса:
```java
@Rule
public ActivityTestRule<MainActivity> activityTestRule =
	new ActivityTestRule<>(MainActivity.class);
```

### Шаг 4. Написание теста

1. Запустите приложение.
2. Посмотрите иерархию элементов с помощью Layout Inspector: [инструкция от Google](https://developer.android.com/studio/debug/layout-inspector).
3. Найдите элемент с текстом «This is home fragment» и его ID.
4. Напишите тест, проверяющий, что у найденного ID текст «This is home fragment».

Шаблон теста:
```java
@Test
public void testName() {
    ViewInteraction mainText = onView(
        withId(R.id.найденный id)
    );
    mainText.check(
        matches(
            withText(Проверяемый текст)
        )
    );
}
```

### Шаг 5. Запуск теста и просмотр отчёта

1. Запустите тест, нажав кнопку запуска возле метода теста.
2. Проверьте, что тест прошёл успешно.
3. Экспортируйте отчёт в html-файл. 

### Шаг 6. Отправка на проверку

1. Выполните commit изменений.
2. Запушьте результат в ранее созданный репозиторий.
3. Отчёт добавьте в issues репозитория на GitHub.
4. Отправьте ссылку на репозиторий на проверку.


# Домашнее задание к занятию «2.6. Espresso»

Любые вопросы по решению задач задавайте в чате учебной группы.

---

## Задание 1. Реализация теста на проверку Intent

### Шаг 1. Запуск проекта в Android Studio

1. Откройте Android Studio.
2. Откройте свой проект из домашнего задания [2.5. Espresso](https://github.com/netology-code/mqa-homeworks/blob/main/2.5%20Espresso/2.5.md).

### Шаг 2. Добавление новых зависимостей

1. Откройте файл /app/build.gradle.
2. Проверьте наличие и при необходимости добавьте зависимости в блок «dependencies»:
```java
     androidTestImplementation 'androidx.test.espresso:espresso-intents:3.4.0'
```

### Шаг 3. Написание теста

1. Выберите один из двух вариантов реализации проверки Intent.
2. Напишите тест на открытие правого меню, проверку элемента «Settings» и нажатие на него.
3. Добавте проверку срабатывания intent ().

Шаблон теста:
```java
//@Rule ... Если вы решили реализовать проверку с использование «Правила»
@Test
public void testName() {
    ViewInteraction element = onView(
        withId(R.id.найденный id)
    );
    element.check(
    matches(Условия проверки);
    //Intents... Если вы решили реализовать проверку с подписыванием на Intent
    element.perform(Клик); //Для запуска intent
    //Проверяем intent, он должен передавать url и action
    //Intents.. 
}
```

### Шаг 4. Запуск теста

1. Запустите тест одним из известных вам способов.
2. Проверьте, что тест прошёл успешно.
3. Экспортируйте отчёт в html-файл.

### Шаг 5. Отправить на проверку

1. Выполните commit изменений.
2. Запушьте результат в ранее созданный репозиторий.
3. Отчёт добавьте в issues репозитория на GitHub.
4. Отправьте ссылку на репозиторий на проверку.

## Задание 2. Реализация теста с использованием Idling Resources

### Шаг 1. Запуск проекта в Android Studio

1. Откройте Android Studio.
2. Откройте свой проект из домашнего задания [2.5. Espresso](https://github.com/netology-code/mqa-homeworks/blob/main/2.5%20Espresso/2.5.md).

### Шаг 2. Добавление новых зависимостей

1. Откройте файл /app/build.gradle.
2. Проверьте наличие и при необходимости добавьте зависимости в блок «dependencies»:
```java
     implementation 'androidx.test.espresso:espresso-idling-resources:3.4.0'
```

### Шаг 3. Написание теста

1. Реализуйте класс Espresso Idling Resources по учебному материалу.
2. Найдите реализацию загрузки списка в коде приложения.
3. Добавьте increment перед началом загрузки списка.
4. Добавьте decrement после загрузки списка.
5. Напишите тест на открытие галлереи и проверку отображения элемента с числом 7.

Шаблон теста:
```java
//@Befor... Здесь подключаемся к счётчику
//@After... Здесь отключаемся от счётчика
@Test
public void testName() {
    ViewInteraction element = onView(
        withId(R.id.найденный id)
    );
    element.perform(Действие);
    element.check(
    matches(Условия проверки);
}
```

### Шаг 4. Запуск теста

1. Запустите тест одним из известных вам способов.
2. Проверьте, что тест прошёл успешно.
3. Экспортируйте отчёт в html-файл.

### Шаг 5. Отправка на проверку

1. Выполните commit изменений.
2. Запушьте результат в ранее созданный репозиторий.
3. Отчёт добавьте в issues репозитория на GitHub.
4. Отправьте ссылку на репозиторий на проверку.


