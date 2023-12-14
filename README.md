# Fragment Test (Tab Experiment)

Nama : Syifa Aurellia Rahma

NIM : 312210009

Kelas : TI.22.A1

Mata Kuliah : Pemrograman Mobile 1


## Tugas
![tugas](https://github.com/syifaaurellia/fragment_test/assets/115867244/fb861b7f-9579-47f3-a830-8cc7d896afbf)



## Fill in All The Code in This Project :
> 1. ***Gradle Script*** => `build.gradle.kts (Module :app)`
```
plugins {
    id("com.android.application")
}

android {
    namespace = "com.tabexperiment"
    compileSdk = 34

    defaultConfig {
        applicationId = "com.tabexperiment"
        minSdk = 21
        targetSdk = 33
        versionCode = 1
        versionName = "1.0"

        testInstrumentationRunner = "androidx.test.runner.AndroidJUnitRunner"
    }

    buildTypes {
        release {
            isMinifyEnabled = false
            proguardFiles(getDefaultProguardFile("proguard-android-optimize.txt"), "proguard-rules.pro")
        }
    }
    compileOptions {
        sourceCompatibility = JavaVersion.VERSION_1_8
        targetCompatibility = JavaVersion.VERSION_1_8
    }
    buildToolsVersion = "34.0.0"
}

dependencies {
    val fragment_version = "1.6.1"
    implementation("androidx.appcompat:appcompat:1.6.1")
    implementation("com.google.android.material:material:1.10.0")
    implementation("androidx.constraintlayout:constraintlayout:2.1.4")
    testImplementation("junit:junit:4.13.2")
    androidTestImplementation("androidx.test.ext:junit:1.1.5")
    androidTestImplementation("androidx.test.espresso:espresso-core:3.5.1")
    implementation("androidx.fragment:fragment:$fragment_version")
}
```
- Setelah itu klik `Sync now`

> 2. ***java***

=> `MainActivity.java`
```
package com.tabexperiment;

import androidx.appcompat.app.AppCompatActivity;
import androidx.viewpager2.widget.ViewPager2;

import android.annotation.SuppressLint;
import android.graphics.drawable.ColorDrawable;
import android.os.Bundle;

import com.google.android.material.tabs.TabLayout;

import java.util.Objects;

public class MainActivity extends AppCompatActivity {

    TabLayout tabLayout;
    ViewPager2 viewPager2;
    ViewAdapter adapter;

    @SuppressLint("NewApi")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Objects.requireNonNull(getSupportActionBar()).setBackgroundDrawable(new ColorDrawable(getColor(R.color.hijautua)));

        tabLayout = findViewById(R.id.tab);
        viewPager2 = findViewById(R.id.view);
        adapter = new ViewAdapter(this);
        viewPager2.setAdapter(adapter);

        tabLayout.addOnTabSelectedListener(new TabLayout.OnTabSelectedListener() {
            @Override
            public void onTabSelected(TabLayout.Tab tab) {
                viewPager2.setCurrentItem(tab.getPosition());
            }

            @Override
            public void onTabUnselected(TabLayout.Tab tab) {

            }

            @Override
            public void onTabReselected(TabLayout.Tab tab) {

            }
        });

        viewPager2.registerOnPageChangeCallback(new ViewPager2.OnPageChangeCallback() {
            @Override
            public void onPageSelected(int position) {
                super.onPageSelected(position);
                tabLayout.getTabAt(position).select();
            }
        });
    }
}
```

=> Membuat file fragment dengan cara klik kanan pada `MainActivity.java` lalu pilih dan klik fragment, setelah itu kita pilih dan klik fragment (Blank), setelah itu kita beri nama `ActionFragment`, `ComedyFragment`, `RomanceFragment`. Untuk file fragment sudah sekaligus dengan file layout xml nya (code berada pada bagian res `layout`)

- `ActionFragment.java` :
```
package com.tabexperiment;

import android.os.Bundle;

import androidx.fragment.app.Fragment;

import android.view.LayoutInflater;
import android.view.Menu;
import android.view.MenuInflater;
import android.view.MenuItem;
import android.view.View;
import android.view.ViewGroup;
import android.widget.Toast;


public class ActionFragment extends Fragment {

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        setHasOptionsMenu(true);
        return inflater.inflate(R.layout.fragment_action, container, false);
    }

    @Override
    public void onCreateOptionsMenu(Menu menu, MenuInflater inflater) {
        inflater.inflate(R.menu.menu_tab, menu);
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        if (item.getItemId() == R.id.tab_action) {
            Toast.makeText(getActivity(), "Clicked on " + item.getTitle(), Toast.LENGTH_SHORT)
                    .show();
        }
        return true;
    }
}
```
- `ComedyFragment.java` :
```
package com.tabexperiment;

import android.os.Bundle;

import androidx.fragment.app.Fragment;

import android.view.LayoutInflater;
import android.view.Menu;
import android.view.MenuInflater;
import android.view.MenuItem;
import android.view.View;
import android.view.ViewGroup;
import android.widget.Toast;

public class ComedyFragment extends Fragment {

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        setHasOptionsMenu(true);
        return inflater.inflate(R.layout.fragment_comedy, container, false);
    }

    @Override
    public void onCreateOptionsMenu(Menu menu, MenuInflater inflater) {
        inflater.inflate(R.menu.menu_tab, menu);
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        if (item.getItemId() == R.id.tab_comedy) {
            Toast.makeText(getActivity(), "Clicked on " + item.getTitle(), Toast.LENGTH_SHORT)
                    .show();
        }
        return true;
    }
}
```

- `RomanceFragment.java` :
```
package com.tabexperiment;

import android.os.Bundle;

import androidx.fragment.app.Fragment;

import android.view.LayoutInflater;
import android.view.Menu;
import android.view.MenuInflater;
import android.view.MenuItem;
import android.view.View;
import android.view.ViewGroup;
import android.widget.Toast;


public class RomanceFragment extends Fragment {

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        setHasOptionsMenu(true);
        return inflater.inflate(R.layout.fragment_romance, container, false);
    }
    @Override
    public void onCreateOptionsMenu(Menu menu, MenuInflater inflater) {
        inflater.inflate(R.menu.menu_tab, menu);
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        if (item.getItemId() == R.id.tab_romance) {
            Toast.makeText(getActivity(), "Clicked on " + item.getTitle(), Toast.LENGTH_SHORT)
                    .show();
        }
        return true;
    }
}
```

=> Lalu buat java class dengan nama `ViewAdapter.java`, yang berisi code :
```
package com.tabexperiment;

import androidx.annotation.NonNull;
import androidx.fragment.app.Fragment;
import androidx.fragment.app.FragmentActivity;
import androidx.viewpager2.adapter.FragmentStateAdapter;

public class ViewAdapter extends FragmentStateAdapter {
    public ViewAdapter(@NonNull FragmentActivity fragmentActivity) {
        super(fragmentActivity);
    }

    @NonNull
    @Override
    public Fragment createFragment(int position) {
        switch (position){
            case 0:
                return new ActionFragment();
            case 1:
                return new ComedyFragment();
            case 2:
                return new RomanceFragment();
            default:
                return new ActionFragment();
        }
    }

    @Override
    public int getItemCount() {
        return 3;
    }
}
```

> 3. ***res***

=> `values`

- `Colors.xml` :
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="blue">#3700B3</color>
    <color name="pink">#FFC0CB</color>
    <color name="colorPrimary">#3F5185</color>
    <color name="colorPrimaryDark">#303F9F</color>
    <color name="colorAccent">#FF4081</color>
    <color name="birumuda">#ABCBFA</color>
    <color name="salem">#F8C6E6</color>
    <color name ="purple">#E3A2ED</color>
    <color name="hijau">#92A676</color>
    <color name="biru">#8FC2EA</color>
    <color name="hijaumuda">#C2E69C</color>
    <color name="kuning">#FFEB3B</color>
    <color name="orange">#FF9800</color>
    <color name="cream">#E6C18A</color>
    <color name="hijautua">#3F4A2F</color>
</resources>
```

=> `themes`

- `themes.xml` dan `themes.xml(night)` (sama isi code nya) :
```
<resources xmlns:tools="http://schemas.android.com/tools">
    <!-- Base application theme. -->
    <style name="Base.Theme.TabExperiment" parent="Theme.MaterialComponents.DayNight.DarkActionBar">
        <!-- Primary brand color. -->
        <item name="colorPrimary">@color/colorPrimary</item>
        <item name="colorPrimaryVariant">@color/biru</item>
        <item name="colorOnPrimary">@color/white</item>
        <!-- Secondary brand color. -->
        <item name="colorSecondary">@color/hijau</item>
        <item name="colorSecondaryVariant">@color/hijaumuda</item>
        <item name="colorOnSecondary">@color/black</item>
        <!-- Status bar color. -->
        <item name="android:statusBarColor">@color/cream</item>
        <item name="android:navigationBarColor">@color/cream</item>
        <!-- Customize your light theme here. -->
    </style>

    <style name="Theme.TabExperiment" parent="Base.Theme.TabExperiment" />
</resources>
```

=> `layout`

- `activity_main.xml` :
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/white"
    tools:context=".MainActivity">


    <com.google.android.material.tabs.TabLayout
        android:id="@+id/tab"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@color/hijau"
        app:tabSelectedTextColor="@color/white"
        app:tabIndicatorColor="@color/white"
        tools:layout_editor_absoluteX="1dp"
        tools:layout_editor_absoluteY="3dp"
        tools:ignore="MissingConstraints">

        <com.google.android.material.tabs.TabItem
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Action"
            tools:layout_editor_absoluteX="0dp"
            tools:layout_editor_absoluteY="3dp" />

        <com.google.android.material.tabs.TabItem
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Comedy" />

        <com.google.android.material.tabs.TabItem
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Romance" />
    </com.google.android.material.tabs.TabLayout>

    <androidx.viewpager2.widget.ViewPager2
        android:id="@+id/view"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_marginTop="50dp"
        android:background="@color/white"
        tools:layout_editor_absoluteX="1dp"
        tools:layout_editor_absoluteY="52dp" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
- `fragment_action.xml` :
```
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".ActionFragment">

    <!-- TODO: Update blank fragment layout -->

    <TextView
        android:id="@+id/action_sinopsis"
        android:layout_width="wrap_content"
        android:layout_height="match_parent"
        android:text="Sinopsis film : Pada pembukaannya, Clint Barton sedang bersama keluarganya di pertanian, namun kebahagiaan mereka hancur ketika putrinya menghilang bersamaan dengan jentikan jari Thanos yang menyebabkan kehancuran besar, menghapus separuh kehidupan di alam semesta. Avengers yang tersisa, termasuk Nebula dan Tony Stark yang kembali ke Bumi, menyusun rencana untuk mencuri kembali Batu Keabadian dan membalikkan tindakan Thanos. Namun, setelah menemukan Thanos telah menghancurkan batu tersebut, mereka berkonfrontasi dengan musuh mereka.  Lima tahun kemudian, Scott Lang kembali dari alam kuantum dan memberi tahu Avengers bahwa mereka dapat menggunakan alam kuantum untuk melakukan perjalanan waktu dan mengambil kembali batu sebelum Thanos menggunakannya. Avengers menyusun rencana dan mengumpulkan kembali anggotanya, termasuk Thor yang kehilangan semangat. Dengan Stark, mereka berhasil mengembangkan mesin waktu dan melakukan perjalanan ke masa lalu untuk mengambil kembali batu-batu keabadian.  Menghadapi berbagai tantangan dan pengorbanan, termasuk kematian Natasha Romanoff, Avengers berhasil mendapatkan batu-batu tersebut. Dalam pertempuran akhir melawan Thanos, Stark mengorbankan dirinya sendiri untuk menggunakan Batu Keabadian dan menghancurkan musuh serta pasukannya. Setelah kemenangan, beberapa anggota Avengers memilih jalannya masing-masing, sementara Captain America memilih menjalani sisa hidupnya di masa lalu bersama Peggy Carter. Sebagai gantinya, ia menyerahkan perisai dan jubah Captain America kepada Sam Wilson."
        android:textAlignment="viewStart"
        android:textAppearance="@style/TextAppearance.AppCompat.Display1"
        android:textSize="16sp"
        android:textStyle="bold" />

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="209dp"
        android:layout_height="1260dp"
        android:src="@drawable/film1" />
</FrameLayout>
```

- `fragment_comedy.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".ComedyFragment">

    <!-- TODO: Update blank fragment layout -->

    <ImageView
        android:id="@+id/imageView2"
        android:layout_width="279dp"
        android:layout_height="1230dp"
        android:src="@drawable/film2" />

    <TextView
        android:id="@+id/comedy_sinopsis"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:text="Sinopsis film : Erwin, seorang lulusan universitas luar negeri, menghadapi dilema antara karir di Singapura dan mengelola toko keluarga karena ayahnya sakit. Erwin, yang awalnya terpaksa mengelola toko, memperbaiki hubungan dengan keluarga dan karyawan toko, menemukan solusi untuk meningkatkan sistem toko, dan membantu memenangkan kompetisi dekorasi. Meski berhasil, tanah toko diincar oleh pengembang properti lokal, dan setelah ayahnya menjualnya, Erwin bersama Yohan berjuang untuk mendapatkan kembali toko mereka.  Kisah berfokus pada pertumbuhan karakter dan hubungan keluarga, dengan Yohan yang mencoba memulai karir sebagai fotografer dan Ayu, istrinya, memiliki impian membuka toko roti. Erwin, setelah menolak promosi, bersama keluarga berjuang untuk mengatasi kegagalan mereka dan mendapatkan kembali toko mereka. Sebuah plot yang penuh emosi, di mana Erwin dan Yohan bersama-sama menemukan kebahagiaan dan memperbaiki hubungan mereka dengan keluarga, memberikan pelajaran tentang kesetiaan, pengorbanan, dan kekuatan keluarga.  Dengan pengungkapan skandal pengembang, kontrak pembelian tanah dibatalkan, dan Erwin memutuskan untuk meninggalkan toko kepada Yohan. Kisah ini mengakhiri dengan keluarga yang memperbaiki hubungan mereka, menunjukkan pertumbuhan karakter yang signifikan dan kekuatan pengorbanan demi keluarga."
        android:textAlignment="viewStart"
        android:textAppearance="@style/TextAppearance.AppCompat.Display1"
        android:textSize="17sp"
        android:textStyle="bold" />
</FrameLayout>
```

- `fragment_romance.xml` :
```
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".RomanceFragment">

    <!-- TODO: Update blank fragment layout -->

    <ImageView
        android:id="@+id/imageView3"
        android:layout_width="222dp"
        android:layout_height="1255dp"
        android:src="@drawable/film3" />

    <TextView
        android:id="@+id/romance_sinopsis"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Sinopsis film :  &quot;20th Century Girl&quot; mengisahkan Na Bo-ra, seorang siswi yang bersumpah untuk mengikuti Baek Hyun-jin demi sahabatnya yang sakit. Namun, Bo-ra malah jatuh cinta pada Poong Woon-ho, sahabat Hyun-jin. Dalam kebingungan cinta segitiga, Bo-ra menyembunyikan perasaannya agar tidak melukai sahabatnya yang ternyata mencintai Woon-ho. Ketika Woon-ho kembali ke Selandia Baru, Bo-ra dan Yeon-du tiba di stasiun kereta pada saat yang tepat, memungkinkan mereka mengakui perasaan mereka sebelum berpisah. Namun, Woon-ho tiba-tiba menghilang dari kehidupan Bo-ra, meninggalkan hatinya yang hancur.  Seiring waktu, Bo-ra masuk universitas dan menjalani kehidupan dewasa. Pada tahun 2019, ia menerima undangan pameran seni dari Joseph, adik laki-laki Woon-ho. Di sini, Bo-ra mengetahui bahwa Woon-ho telah meninggal dalam kecelakaan bertahun-tahun yang lalu. Joseph bersyukur pada Bo-ra karena mengenang saudaranya dan mengungkapkan bahwa momen terbahagia Woon-ho adalah bersama Bo-ra. Saat melihat video yang dibuat Woon-ho, Bo-ra merenung tentang kenangan indah yang mereka bagikan.  Dengan latar tahun 1999 dan 2019, &quot;20th Century Girl&quot; membawa penonton dalam perjalanan emosional Bo-ra yang penuh kebingungan cinta, pertemanan, dan kehilangan. Film ini menggambarkan kompleksitas hubungan manusia seiring waktu, dengan kisah yang menyentuh hati dan meninggalkan kesan mendalam."
        android:textAlignment="viewStart"
        android:textAppearance="@style/TextAppearance.AppCompat.Display1"
        android:textSize="17sp"
        android:textStyle="bold" />

</FrameLayout>
```
=> Pada directory `drawable` kita bisa tambahkan gambar untuk pict dari film yang ingin kita tampilkan, dan jangan lupa untuk menambahkan icon `baseline_more_vert_24.xml` dengan cara klik kanan pada `drawable` lalu klik New, setelah itu kita pilih dan klik Vector Asset. Setelah itu kita klik clip art lalu kita pilih icon nya, jika sudah ketemu kita klik OK lalu kita klik next

=> Selanjutnya kita klik kanan pada `app` lalu pilih dan klik `Android Resource Directory` setelah itu kita beri nama "menu" lalu klik OK. Setelah itu kita buat Menu Resource File dengan nama `menu_tab.xml` lalu isi dengan code :
```
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:tools="http://schemas.android.com/tools"
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">
    <item
        android:id="@+id/tab_action"
        android:icon="@drawable/baseline_more_vert_24"
        android:title="Action"/>

    <item
        android:id="@+id/tab_comedy"
        android:icon="@drawable/baseline_more_vert_24"
        android:title="Comedy"/>

    <item
        android:id="@+id/tab_romance"
        android:icon="@drawable/baseline_more_vert_24"
        android:title="Romance"/>
</menu>
```

> Hasil Run :



https://github.com/syifaaurellia/fragment_test/assets/115867244/40848674-e30a-4b2d-8c22-cf735496ae66


## Selesai, Terima Kasih 
