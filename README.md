# Отчёт о тестировании 

## Краткое описание

11.03.2020 - 11.03.2020 было проведено Функциональное тестирование работы приложения Credit Card Number Validator

На тестирование затрачено: 1 час

В результате тестирования выявлены следующие дефекты:
* [Деффект 1](https://github.com/pldenn/java1/issues/1)
* [Деффект 2](https://github.com/pldenn/java1/issues/2)

## Описание процесса тестирования

В процессе тестирования использовались следующие артефакты*:
* [Руководство по установке IntelliJ IDEA](idea.md)
* Код программы [Credit Card Number Validator](artifacts/Main.java)


В качестве тестовых данных использовались данные :

```java
public class Main {
  public static void main(String[] args) {
    // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
    String number = "5351719427810741";
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
  }

  public static boolean isValidCardNumber(String number) {
    if (number == null) {
      return false;
    }

    if (number.length() != 16) {
      return false;
    }

    long result = 0;
    for (int i = 0; i < number.length(); i++) {
      int digit;
      try {
        digit = Integer.parseInt(number.charAt(i) + "");
      } catch (NumberFormatException e) {
        return false;
      }

      if (i % 2 == 0) {
        digit *= 2;
        if (digit > 9) {
          digit -= 9;
        }
      }
      result += digit;
    }

    return (result != 0) && (result % 10 == 0);
  }
}
```
Скриншот запуска
![](pic/bag.png)


#### Валидные ключи:

* 5351719427810741 
* 6351719427810741
* 351719427810741

Тестирование производилось в следующем окружении:
* Windows 7 Профессиональная 64
* OpenJDK version 11.0.6
* IntelliJ IDEA 2019.3.3

