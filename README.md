# Лабораторная работа №2. Основы верстки.
Выполнила: Усова Валентина, ИСП-221С
## Что делает приложение?

Приложение с четырьмя экранами предлагает пользователю различные функции, доступные через меню с кнопками на главном экране.

## Работа приложения

### 1.  MainActivity
• Содержит меню из четырех кнопок, занимающих 20% высоты экрана с 2% расстоянием между ними.
• Кнопки выровнены по центру экрана, занимают 75% его ширины и находятся на равном расстоянии от краев.
   ![image](https://github.com/user-attachments/assets/a81ef191-68ec-488a-953c-c8c54cdb55bf)
   


### 2.  Activity2
• Доступен после нажатия на первую кнопку на главном экране.
• Верстка выполнена с помощью LinearLayout.
  ![image](https://github.com/user-attachments/assets/19a9deef-a521-442e-af06-8632e28cf597)

### 3.  Activity3
• Доступен после нажатия на вторую кнопку на главном экране.
• Верстка выполнена с помощью RelativeLayout.


### 4.  Activity4
• Доступен после нажатия на третью кнопку на главном экране.
• Кнопка выровнена по центру экрана с обводкой серого цвета (#505050) толщиной, соответствующей месяцу рождения пользователя (от 1 до 12).
• Радиус скругления кнопки 24dp.
• Фон экрана белый (#FFFFFF).
• При нажатии на кнопку ее цвет меняется на светло-зеленый.

  
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
