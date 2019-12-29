# SimpleDataBindingEx
SimpleDataBinding Example with Android Architecture Jetpack

DataBinding:
The Data Binding Library is a support library that allows us to bind user interface components in our layouts to data sources.

 So, we can tie the UI with business logic, which allows the UI values to update automatically.

Benefits:

·      Not to use findViewById() again.

·      You don’t have to create an adapter for every list, recycler view, or pager in the app.

·      You can easily and efficiently handle callbacks.

·      Using two-way data binding you can implement forms in your app effectively.

There are two things we need to do before start using databinding.

1.   Make sure this android support repository installed.

(go to tools=>sdk manager=>sdk tools)
2.   Enable Data Binding on the app level gradle file.
android {
    compileSdkVersion 29
    dataBinding{
        enabled = true
    }
    }
    
3.add layout tag on xml files 
<layout>
    <data>
        <variable
            name="student"
            type="com.gokul.tut.simpledatabindingex.Student" />
    </data>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/tv_sr_title"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="40dp"
        android:text="Student Registration"
        android:textStyle="bold"
        android:textSize="24sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
</constraintLayout>
<layout>

4.Instead of invoking findviewbyId 
mainBinding = DataBindingUtil.setContentView(this,R.layout.activity_main);
        mainBinding.setStudent(getCurrentStudent());
        
5.we can pass values to the layout directly using 
<TextView
        android:id="@+id/tv_sr_name"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="@{student.name}"
        android:textStyle="bold"
        android:textSize="24sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/tv_sr_title" />
        
  <TextView
        android:id="@+id/tv_sr_email"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="8dp"
        android:text="@{student.email}"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/tv_sr_name" />


