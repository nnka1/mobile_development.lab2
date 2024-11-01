# Лабораторная работа №1. Создание Activity и передача параметров между ними.
Выполнила: Усова Валентина, ИСП-221С
## Что делает приложение?

Приложение демонстрирует простой пример передачи данных между двумя активити. 

## Работа приложения

### 1.  MainActivity
1.1 Отображает кнопку btn1.

1.2. При нажатии на кнопку:
* Создается Intent для запуска MainActivity2.
* В Intent передается параметр "familyName" со значением "Усова". 
* Вызывается метод startActivity() для запуска MainActivity2.
   ![image](https://github.com/user-attachments/assets/a81ef191-68ec-488a-953c-c8c54cdb55bf)
   


### 2.  MainActivity2

2.1. Получает переданный параметр "familyName" из Intent.

2.2 Отображает значение параметра в текстовом поле.

  ![image](https://github.com/user-attachments/assets/19a9deef-a521-442e-af06-8632e28cf597)
  
## Как собрать проект?
1. Загрузка или клонирование репозитория:
* Скачайте файлы проекта (ZIP-архив) и разархивируйте их в удобную папку или клонируйте репозиторий с помощью команды git clone [URL репозитория].

2. Открытие проекта в Android Studio:
* Откройте Android Studio.
* В главном окне выберите "Open an existing Android Studio project".
* Найдите папку, в которую вы скачали или клонировали проект, и выберите файл build.gradle.

3. Запуск приложения:
* В Android Studio, нажмите кнопку "Run" (зеленый треугольник) на панели инструментов.
* Выберите эмулятор или подключенное Android-устройство, на котором вы хотите запустить приложение.
* Дождитесь завершения сборки и запуска приложения.

## Исходный код:
### MainActivity
```
package com.example.myapplication

import android.os.Bundle
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.ViewCompat
import androidx.core.view.WindowInsetsCompat
import android.widget.Button
import android.content.Intent


class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        enableEdgeToEdge()

        val button = findViewById<Button>(R.id.btn1)

        button.setOnClickListener {
            val intent = Intent(this, MainActivity2::class.java)
            intent.putExtra("familyName", "Усова")

            startActivity(intent)
        }

    }
}
```
### MainActivity2
```
package com.example.myapplication

import android.os.Bundle
import android.widget.TextView
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.ViewCompat
import androidx.core.view.WindowInsetsCompat

class MainActivity2 : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main2)

        val familyName = intent.getStringExtra("familyName")

        val textView = findViewById<TextView>(R.id.textView)
        textView.text = "переданный параметр: $familyName"
    }
}
```
### activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#6997D3"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/btn1"
        android:layout_width="178dp"
        android:layout_height="87dp"
        android:backgroundTint="#05326D"
        android:text="нажми меня"
        android:textSize="20sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="HardcodedText" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
### activity_main2.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#717DD7"

    tools:context=".MainActivity2">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:fontFamily="sans-serif"
        android:text="TextView"
        android:textColor="#081472	"
        android:textSize="20sp"
        android:textStyle="bold"
        android:typeface="normal"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
