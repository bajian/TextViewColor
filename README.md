# TextViewColor
Html.fromHtml


//android TextView、EditText对部分内容设置颜色、字体、超链接、图片; 
    //这里是以一个TextView为例子，EditText的设置方法和TextView一样

    //TextView对象
    TextView txtInfo = new TextView(this);

    //文本内容
    SpannableString ss = new SpannableString("红色打电话斜体删除线绿色下划线图片:.");

    //设置0-2的字符颜色
    ss.setSpan(new ForegroundColorSpan(Color.RED), 0, 2,Spanned.SPAN_EXCLUSIVE_EXCLUSIVE);

    //设置2-5的字符链接到电话簿，点击时触发拨号
    ss.setSpan(new URLSpan("tel:4155551212"), 2, 5,Spanned.SPAN_EXCLUSIVE_EXCLUSIVE);
    
    //设置9-11的字符为网络链接，点击时打开页面
    ss.setSpan(new URLSpan("http://www.hao123.com"), 9, 11,Spanned.SPAN_EXCLUSIVE_EXCLUSIVE);

    //设置13-15的字符点击时，转到写短信的界面，发送对象为10086
    ss.setSpan(new URLSpan("sms:10086"), 13, 15,Spanned.SPAN_EXCLUSIVE_EXCLUSIVE);

    //粗体
    ss.setSpan(new StyleSpan(Typeface.BOLD_ITALIC), 5, 7,Spanned.SPAN_EXCLUSIVE_EXCLUSIVE);

    //斜体
    ss.setSpan(new StyleSpan(android.graphics.Typeface.ITALIC), 7, 10,Spanned.SPAN_EXCLUSIVE_EXCLUSIVE);

  //下划线
    ss.setSpan(new UnderlineSpan(), 10, 16,Spanned.SPAN_EXCLUSIVE_EXCLUSIVE);

  //以下代码是在指定位置插入图片
    Drawable d = getResources().getDrawable(R.drawable.icon);

    //设置图片大小
    d.setBounds(0, 0, d.getIntrinsicWidth(), d.getIntrinsicHeight());

    //插入的位置
    ss.setSpan(new ImageSpan(d, ImageSpan.ALIGN_BASELINE), 18, 19, Spannable.SPAN_INCLUSIVE_EXCLUSIVE);

    //设置文本内容到textView
    txtInfo.setText(ss);

    //不添加这一句，拨号，http，发短信的超链接不能执行.
    txtInfo.setMovementMethod(LinkMovementMethod.getInstance());
