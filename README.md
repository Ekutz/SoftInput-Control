# 소프트 키보드 제어하기

EditText와 쌍을 이루어 타자를 입력할 수 있게 해주는 소프트 키보드. 하지만 뜻대로 움직이지 않는 경우가 부지기수이다. 이를 제어하여 어플을 잘 만들어 보자

## 자동 포커스

EditText가 포함된 액티비티에서는 자동으로 EditText에 포커스를 맞춰 액티비티가 시작될때 키보드가 나오는 경우가 있다.

![problem1](https://github.com/Ekutz/SoftInput-Control/blob/master/problem.gif?raw=true)

이를 방지해보자.

### 키보드 감추기

코드에서 InputMethodManager를 이용하여 키보드를 나오지 않도록 만든다.

**MainActivity.java**

```
InputMethodManager im =
(InputMethodManager)getSystemService(Context.INPUT_METHOD_SERVICE);

im.hideSoftInputFromWindow(editText.getWindowToken(), 0);

```

## 뷰 가림

제멋대로 튀어나오는 키보드는 처리했지만 여전히 아래쪽의 뷰가 가려지는 건 어쩔 수 없는 걸까? 이를 해결해 보자

### 액티비티 속성 추가

**AndroidManifest.xml**

```
<activity android:name=".MainActivity"
		  android:windowSoftInputMode="adjustResize">

```

windowSoftInputMode를 추가하여 가려진 뷰를 보자

