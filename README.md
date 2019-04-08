activity_main.xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_marginTop="100dp"
    android:orientation="vertical" >

    <TextView
        android:id="@+id/txt"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="26dp"
        android:text="用于测试的内容"/>

    <Button
        android:id="@+id/button3"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/txt"
        android:gravity="center"
        android:text="next"

        />
</LinearLayout>

menu_main

    <item android:title="字体大小"
        >
        <menu>
            <!--定义一组选项菜单-->
            <group android:checkableBehavior="single">
                <!--定义多个菜单项-->
                <item
                    android:id="@+id/font_10"
                    android:title="小"/>
                <item
                    android:id="@+id/font_16"
                    android:title="中"/>
                <item
                    android:id="@+id/font_20"
                    android:title="大"/>
            </group>
        </menu>
    </item>
    <!--定义一个普通菜单项-->
    <item android:id="@+id/plain_item"
        android:title="普通菜单项"/>
    <item android:title="颜色"
       >
        <menu>
            <!--定义一个普通选项菜单-->
            <group>
                <!--定义三个菜单项-->
                <item
                    android:id="@+id/red_font"
                    android:title="红色"/>
                <item
                    android:id="@+id/black_font"
                    android:title="黑色"/>
            </group>
        </menu>
    </item>
</menu>

mainactivity

  public class MainActivity extends AppCompatActivity {
    
    private TextView textView;
    
    private Button nexbut;
    
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        textView = (TextView) findViewById(R.id.txt);
        nexbut = findViewById(R.id.button3);

    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        MenuInflater inflater = new MenuInflater(this);
        inflater.inflate(R.menu.menu_main,menu);
        return super.onCreateOptionsMenu(menu);
    }
   

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        if (item.isCheckable()){
            //勾选菜单项
            item.setCheckable(true);
        }
        //switch 判断单击哪个菜单项，并有针对性的做出响应
        switch (item.getItemId()){
            case R.id.font_10:
                textView.setTextSize(10 * 2);
                break;
            case R.id.font_16:
                textView.setTextSize(16 * 2);
                break;
            case R.id.font_20:
                textView.setTextSize(20 * 2);
                break;
            case R.id.red_font:
                textView.setTextColor(Color.RED);
                break;
            case R.id.black_font:
                textView.setTextColor(Color.BLACK);
                break;
            case R.id.plain_item:
                Toast.makeText(this, "这是一个普通菜单选项",
                        Toast.LENGTH_SHORT).show();
                break;
            default:
                break;

        }
        return true;
    }
}

  结果截图总界面：https://github.com/linyu0119/UIexample3/blob/master/images/1.png
  测试字体：https://github.com/linyu0119/UIexample3/blob/master/images/2.png
  测试toast提示：https://github.com/linyu0119/UIexample3/blob/master/images/3.png
  测试颜色：https://github.com/linyu0119/UIexample3/blob/master/images/4.png

