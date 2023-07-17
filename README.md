# دوره مقدماتی آموزش سیستم عامل ROS

![تصویر معرفی سیستم عامل ربات](image.png)

سیستم عامل ربات ها (ROS)، بستری قدرتمند و سریع را برای یکپارچه سازی کدهای مربوط به هر یک از واحدهای ربات فراهم می سازد. به کمک سیستم عامل ربات ها می توانید تحت لینوکس کد مربوط به هر یک از واحدهای فوق را در یک گره (Node) بنویسید و ارتباط موثر بین این گره ها را از طریق پیام هایی (Topic) ایجاد کنید. سیستم عامل ربات ها یا همان ROS علاوه بر ایجاد یک ساختار منظم و کاربردی برای توسعه ربات ها، پکیج هایی استاندارد برای کاربردهای بینایی، کنترل و درایو، طراحی مسیر، نمایش داده ها و ... فراهم می کند. در این آموزش ما قصد داریم تا با این سیتسم عامل رباتیک آشنا شویم. مباحث این آموزش:

- آشنایی با مقدمات و چارچوب کلی سیستم عامل ربات
- آشنایی با دستورات مهم لینوکس
- آموزش نصب ROS، ایجاد محیط کاری و ایجاد اولین پکیج
- آشنایی با نحوه ایجاد گره ها و تاپیک ها
- آشنا با پیام ها و سرویس ها
- آشنایی با پارامترها
- امکانات کاربردی سیستم عامل ROS
- آشنایی با فایل launch
- آشنایی با TFها
- زمان در ROS
- اجرای تحت شبکه ROS
- ارتباط Action در سیستم عامل ROS
- آشنایی با تنظیمات دینامیک
- آشنایی با محیط rviz و اجرای چند مثال کاربردی

در ادامه به برسی هر کدام از عناوین مطرح شده می پردازیم. لازم به ذکر است که در آینده آموزش ویدیویی ضبط و لینک آن به این صفحه اضافه خواهد شد. توجه شود که این آموزش در برگیرنده مطالب در مورد نسخه اول سیستم عامل رباتیک (ROS) می باشد.

- [آشنایی با مقدمات و چارچوب کلی سیستم عامل ربات](#آشنایی-با-مقدمات-و-چارچوب-سیستم-عامل-ربات)
- [آشنایی با دستورات مهم لینوکس](#آشنایی-با-دستورات-ابتدایی-لینوکس)
- [آموزش نصب ROS، ایجاد محیط کاری و ایجاد اولین پکیج](#آشنایی-با-نحوه-نصب-ros-ایجاد-محیط-کاری-و-اولین-پکیج)
- [آشنایی با نحوه ایجاد گره ها و تاپیک ها](#آشنایی-با-نحوه-ایجاد-گره-ها-و-تاپیک-ها)
- [آشنا با پیام ها و سرویس ها](#آشنا-با-پیام-ها-و-سرویس-ها)
- [آشنایی با پارامترها](#آشنایی-با-پارامترها)
- [آشنایی با rosbag](#آشنایی-با-rosbag)
- [آشنایی با roswtf](#آشنایی-با-roswtf)
- [آشنایی با ابزارهای rqt](#آشنایی-با-ابزارهای-rqt)
- [واحد های استاندارد](#واحد-های-استاندارد)
- [آشنایی با فایل های launch](#آشنایی-با-فایل-های-launch)

## آشنایی با مقدمات و چارچوب سیستم عامل ربات

همان گونه که ذکر شد سیستم عامل ربات (ROS) یک چارچوب (Framework) برای توسعه استاندارد و سریع برنامه های رباتیکی می باشد که از مزایای اصلی این چارچوب می توان به متن باز (Open-Sourse) و حاوی پکیج و ابزارهای کاربردی بودن اشاره کرده. این پکیج در سال 2009 توسط یک استارت آپ به نام Willow Garage و توسط دو فرد به نام های Eric Berger و Keenan Wyrobek توسعه یافته است و از حدود سال 2014 به صورت متن باز منتشر شده است. لیست ورژن های مختلف این سیستم عامل را می توانید در لینک زیر مشاهده نمایید:

https://wiki.ros.org/Distributions

یکی از دلایل استفاده از سیستم عامل ربات (ROS) این است که در اکثر پروژه های رباتیک ما با چالش هایی برای درایور کردن عملگرها (Actuators) و حسگرها (Sensors) و اجرای این بخش اگر قرار باشد از صفر صورت بپذیرد، علاوه بر وقت گیر بودن، ما را باگ ها و مشکلات فراوان در مراحل بعدی روبرو می کند.سیستم عامل ربات شرایطی را برای ما فراهم می کنید تا ما صرفاً بر روی بخش منطق ربات کار کنیم و برای دو بخش حسگرها و عملگرها از پکیج های استاندارد ROS بهره ببریم. از مزایای دیگر سیستم عامل ربات می توان به سازگار بودن با زبان های مختلف (بالاخص زبان C++ , پایتون)، مناسب برای رشته های و حوزه های مختلف، بروزرسانی دائمی و جامعه کاربری بزرگ اشاره کرد. همچنین پکیج هایی که توسط ما بر چارچوب ROS ایجاد می شوند، قابلیت استفاده مجدد در کنار سایر پروژه ها (ما یا دیگران) را دارند.

![تصویر ساختار کلی ربات](image-1.png)

سیستم عامل ربات (ROS) به ما این امکان را می دهد تا یک برنامه رباتیکی را به بخش های مختلف تقسیم کنیم که هر کدام از این بخش ها یک گره (Node) می باشد. این نودها می توانند به روش های مختلف با یک دیگر مرتبط باشند:

- تاپیک ها (Topics)
- سرویس ها (Services)
- اکشن ها (Actions)

![نودها در  سیستم عامل ربات](image-2.png)

در نوع ارتباطی تاپیک، یک نود وظیفه انتشار اطلاعات را دارد که به آن Publisher می گویند و به سایر گره ها که اطلاعات را دریافت می کند، Subscriber می گویند. توجه شود که این ارتباطات مداوم است. یعنی پس اتصال این دو گره به هم اطلاعات با فرکانس خاصی به صورت مداوم رد و بدل می شود. نوع بعدی ارتباط سرویس ها می باشد. در این روش ارتباطی یک گره سرور و یک گره کلاینت داریم. در ابتدا هرگاه کلاینک به اطلاعات نیاز داشته باشد به سرور یک درخواست (Request) و سرور نیز در جواب پس از انجام پردازش هایی، اطلاعات را پاسخ (Respond) می دهد. در این روش ارتباطی در بازه زمانی که درخواست ارسال شده تا لحظه دریافت پاسخ، برنامه کلاینت متوقف باقی می ماند. روش سرویس زمانی که پردازش های سرور طولانی باشد یا ما بخواهیم در حین این زمان پردازشی انجام دهیم فاقد کاربرد می شود؛ پس برای این حالت به سراغ روش سوم می رویم که اکشن نام دارد و مشابه سرویس ها است با این تفاوت که در بین زمان ارسال درخواست و دریافت پاسخ، برنامه متوقف نمی شود.

![راه های ارتباطی گره ها](image-3.png)

این روش های ارتباطی در بخش های بعدی برسی بیشتر خواهد شد. لازم به ذکر است که برای توسعه هر نود می توان از زبان های مختلف استفاده کرد، البته API ارایه شده برای پایتون و سی پلاس پلاس استاندارد تر است.

## آشنایی با دستورات ابتدایی لینوکس

در این بخش قصد داریم تا برخی از دستورات (command) معروف سیستم عامل لینوکس را با هم مرور کنیم. این دستورات در محیط ترمنیال (Terminal) لینوکس استفاده می شود و تا حدود زیادی کار ما را در محیط لینوکس راحت می کند. در بخش زیر می توانید لیست این کامند ها را با توضیحات مربوطه مرور نمایید:

```bash
# Sending ping packets to a ip or address
$ ping [ip/address] -c [number-of-packets]

# Open Manual of a linux command
$ man [command-name]

# List the recent directory files and dirs
$ ls

# Navigate to a dir
$ cd [directory-name]

# Show the active directory address from root
$ pwd

# Create a directory
$ mkdir [dir-name]

# Create a file
$ touch [file-name]

# Open a file with editor
$ nano/gedit/code [file-name]

# Remove a file
$ rm [file-name]

# Remove a dir
$ rm -r [dir-name]
#or
$ rmdir [dir-name]

# Dir tree
$ tree # install: sudo apt-get install tree

# Copy files
$ cp [file-name] [goal-dir] [new-name]

# Move files
$ mv [file-name] [goal-dir] [new-name]

# Add Executability to a file
$ chmod +x [file-name]

# Shut down
$ poweroff

# Restart
$ reboot
```

توجه شود که در ترمینال منظور از ~ شاخه Home و منظور از / شاخه root می باشد.

## آشنایی با نحوه نصب ROS، ایجاد محیط کاری و اولین پکیج

در این بخش قصد داریم تا به نحوه نصب سیستم عامل ربات بپردازیم، سپس به نحوه ایجاد یک فضای کاری استاندارد برویم و اولین پکیج خودمان را نیز ایجاد نماییم. برای نصب ورژن Neotic سیستم عامل ROS می توانید به لینک زیر مراجعه نمایید:

http://wiki.ros.org/ROS/Installation

دستورات نصب به صورت خلاصه با کامنت در بخش زیر آورده شده است.

```bash
# Add the ros rep to apt dir
$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

# Install curl
$ sudo apt install curl # if you haven't already installed curl

# load curl asc file and pass key
$ curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -

# Update the apt rep
$ sudo apt update

# Install ROS neotic
$ sudo apt install ros-noetic-desktop-full

# Add ros to Enviromental vars
$ echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc

# Source the bashrc file
$ source ~/.bashrc

```

پس از نصب ROS برای چک کردن اینکه آیا موفق می توانید کامند زیر هسته ROS را اجرا می نماید تست کنید:

```bash
$ roscore
```

همچنین با کامند زیر می توانید به محل نصب پکیج های ROS بروید:

```bash
$ cd /opt/ros/noetic/share/
```

پکیج های موجود در دایرکتوری بالا در واقع لیست پکیج هایی هستند که به صورت پیشفرض بر روی ROS فول ورژن موجود هستند. اگر پکیجی را در این دایرکتوری قرار دهید، می توانید از آن به صورت گلوبال بدون نیاز به اضافه کردن مجدد بهره ببرید. در کل با کمک دستور زیر می توانید، لیست محل هایی که پکیج های راس ذخیره می شوند را مشاهده نمایید:

```bash
$ echo $ROS_PACKAGE_PATH
```

همچنین ROS کامندهای برای مشاهده پکیج ها و اطلاعات آنها دارد. برخی از این کامندها (در ادامه نیز در بسته به نیاز بخش مربوطه کامنت هایی ارایه خواهند شد):

- برای مشاهده محل نصب یک پکیج (برای مثال پکیج roscpp) می توانید از دستور زیر کمک بگیرید:

```bash
$ rospack find roscpp
```

- همچنین برای رفتن به محل نصب آن، می توانید از دستور زیر بهره بگیرد:

```bash
$ roscd roscpp
```

- همچنین برای مشاهده محتویات یک پکیج می توانید از دستور زیر بهره ببرید:

```bash
$ rosls roscpp
```

همچنین با قرار دادن help جلوی سه کامند ذکر شده می توانید، با عملکرد بیشتر این پکیج ها آشنا شوید.
(از سوئیچر -h نیز می توان استفاده کرد.)

اکنون که ROS را با موفقیت نصب کردیم به سراغ ایجاد یک فضای کاری می رویم. فضای کار مجازی یا Virtual environment یک محیط استاندارد است که فایل کدهای خود را در داخل آن قرار می دهیم. برای ایجاد این محیط ابتدا یک پوشه به نام catkin_ws ایجاد کرده و همچنین در داخل آن یک دایرکتوری خالی به نام src ایجاد می کنیم. سپس کامند زیر را اجرا می کنیم تا کامپایلر ROS این محیط را برای ایجاد کند.

```bash
$ catkin_make
```

محیط کاری ما با موفقیت ایجاد شده. لازم به ذکر است در مراحل بعدی هرگاه نیاز شد مجدد برنامه را کامپایل کنیم، حتما به شاخه اصلی catkin_ws آمده و کامند بالا را اجرا کنید.

اکنون که محیط کاری مجازی را آماده کردیم، می توانیم به سراغ ایجاد اولین پکیج خود برویم. برای ایجاد پکیج کافی است به داخل پوشه src محیط کاری کتکین خود برویم و با کمک فرمت دستوری زیر یک پکیج ایجاد کنیم:

```bash
$ cd ~/catkin_ws/src
$ catkin_create_pkg <package_name> [depend1] [depend2] [depend3]
```

برای مثال:

```bash
$ catkin_create_pkg beginner_tuts std_msgs rospy roscpp
```

بعد مجدد به پوشه catkin_ws مراجعه شود و مجدد با دستور catkin_make کامپایل انجام شود. و همچنین دستور را در فایل bashrc قرار دهیم. (توجه شود که اگر در دایرکتوری هوم، ورک اسپیس را ایجاد نکرده اید آدرس زیر را اصلاح کنید!)

```bash
$ source ~/catkin_ws/devel/setup.bash
```

همچنین برای مشاهده پیش نیازها و dependencies های یک پکیج می توانید از دستور زیر کمک بگیرید (دستور زیر فقط پیش نیازهای مرحله اول را نمایش می دهد):

```bash
$ rospack denpend1 [package-name]
```

در صورتیکه بخواهید تمام پیش نیاز ها را ببینید از دستور زیر بهره بگیرید:

```bash
$ rospack denpend [package-name]
```

نکته: در فایل package.xml اطلاعات پکیج، ورژن، پیشنیاز ها و سایر اطلاعات نمایش داده می شود.

نکته: در فایل CMakeLists.txt مربوط به تنظمیات کامپایلر می باشد که لیست پکیج های پیشنیاز، پیام ها، سرویس ها، اکشن ها، اطلاعات کامپایل و ... قرار گرفته است و معمولا اگر قرار باشد یک نود با سی پلاس پلاس نوشته شود، با این فایل بسیار کار می شود.

برای دریافت اطلاعات بیشتر به صفحه خود داکیومنت راس به آدرس زیر مراجعه شود:

http://wiki.ros.org/ROS/Tutorials/CreatingPackage

## آشنایی با نحوه ایجاد گره ها و تاپیک ها

در این قسمت قصد داریم تا در مورد نحوه ایجاد گره ها (Nodes) و نحوه ایجاد تاپیک (Topics) توضیحاتی را ارایه کنیم. در ابتدا قبل ایجاد یک گره و تاپیک، چند گره معروف در ROS را اجرا میکنم. در این سیستم عامل یک پکیج با نام turtlesim وجود دارد که برای تست کردن دستورات ROS مورد استفاده قرار می گیرد. برای اجرای هر برنامه ROS نیاز است تا ابتدای کار هسته آن اجرا شود. هسته همانگونه که زودتر بیان شد با کامند زیر اجرا می شود:

```bash
$ roscore
```

برای اجرای نودها نیز از کامند زیر بهره می بریم:

```bash
$ rosrun [package-name] [node-name]
```

برای مثال برنامه لاکپشت را اجرا می کنیم، این برنامه به دو نود turtlesim_node و turtle_teleop_key را اجرا نماییم:

```bash
$ roscore
$ rosrun turtlesim turtlesim_node
$ rosrun turtlesim turtle_teleop_key
```

خروجی این برنامه به شکل زیر خواهد بود. با تغییر دکمه های موس در ترمینال مربوط به turtle_teleop_key لاکپشت شروع به حرکت می کند.

![Alt text](image-4.png)

در ادامه به برسی برخی از دستورات کاربردی در مورد گره ها و تاپیک ها می پردازیم. شما می توانید با تکرار این دستورها با برنامه turtle این دستورات را تمرین نمایید:

برای مشاهده اطلاعات یک نود از دستور زیر استفاده کنید:

```bash
$ rosnode info /rosout
```

ّبرای اجرای یک نود از یک پکیج از دستور زیر استفاده نمایید:

```bash
$ rosrun [package-name] [node-name]
```

ّتوجه شود که نودهای داخل راس تحت شبکه اجرا می شود، برای پینگ گرفتن از یک نود از دستور زیر می توان بهره برد:

```bash
$ rosnode ping /rosout
```

برای مشاهده گراف نودها می توانید از دستور زیر بهره ببرید:

```bash
$ rosrun rqt_graph rqt_graph
```

یا دستور زیر را به صورت خلاصه وارد کنید (از نئوتیک ب بعد):

```bash
$ rqt_graph
```

برای مشاهده اطلاعات یک تاپیک می توانید از دستور rostopic بهره ببرید، برای اطلاع کامل از این دستور کامند زیر را وارد نمایید تا help آنرا مشاهده نمایید:

```bash
$ rostopic -h
```

برای مثال با کمک دستور زیر می توانید لیست تاپیک ها را ببیند:

```bash
$ rostopic list
```

نکته: برای مشاهده لیست تاپیک ها به صورت دسته بندی شده، از دستور زیر بهره می بریم:

```bash
$ rostopic list -v
```

با کمک دستور زیر می توانید پیام های رد و بدل شده در یک تاپیک را مشاهده کنید:

```bash
$ rostopic echo /topic-name
```

با کمک دستور زیر می توانید نوع تاپیک را مشاهده نمایید:

```bash
$ rostopic type /topic-name
```

برای پابلیش کردن دیتا در یک تاپیک می توانید از دستور rostopic pub این کار را انجام دهید، البته قبل از آن نیاز است تا ساختار تاپیک را بدانیم، با کمک دستور زیر می توانید ساختار تاپیک (نوع message) را مشاهده کنید:

```bash
$ rosmsg show [message-name]
```

و سپس با دستور زیر داخل تاپیک پیام دلخواه خود را منتشر کنید:

```bash
$ rostopic pub [topic-name] [message-type] data
```

توجه شود اگر نتوانستید نوع مسیج را تایپ کنید از کلید TAB استفاده نمایید، همچنین اگر نتوانستید ساختار دیتا را وارد نمایید، دوباره TAB را بزنید. (ویدیو را ببنید متوجه می شوید)

برای متناوب کردن دستور پاب می توانیم از سوئیچر -r بهره ببریم:

```bash
$ rostopic pub [topic-name] [message-type] data -r 3
```

برای مثال در کامند بالا گفتیم با فرکانس 3 هرتز حرکت ذکر شده را تکرار کن!

با کمک دستور زیر می توانیم فرکانس پابلیش یک پیام در یک تاپیک را مشاهده کنیم

```bash
$ rostopic hz [topic-name]
```

برای پلات کردن یک تاپیک می توانید از پنجره rqt_plot بهره ببرید:

```bash
$ rosrun rqt_plot rqt_plot
```

در ادامه به نحوه ایجاد دو عدد گره برای تبادل پیام در بستر یک تاپیک می پردازیم. ابتدا این نودها را با کمک سی پلاس پلاس ایجاد می کنیم و سپس به سراغ پایتون می رویم. برای ایجاد یک تاپیک کافی است به پکیج خود و در پوشه src بروید و یک فایل ایجاد کنید، برای مثال می خواهیم دو نود ایجاد کنیم، یک نود فرستنده و یک نود دریافت کنند که با یک تاپیک با هم در ارتباط هستند. در ابتدا با کمک کامند زیر به پوشه پکیج خود بروید:

```bash
$ roscd beginner_tutorials
```

سپس به پوشه src بروید و با کمک کامند زیر نود مربوط به فرستنده (talker) ایجاد نمایید. در ابتدا در سی پلاس پلاس را توضیح می دهیم سپس به سراغ نوع پایتونی می رویم:

```bash
$ cd src
$ touch talker.cpp
```

اکنون در داخل فایل ایجاد شده کد زیر را قرار می دهیم (در کامنت های کد زیر، توضیحات خلاصه و البته کافی داده شده است):

```c++
// Adding ROS Libs to our cpp code
#include "ros/ros.h"
#include "std_msgs/String.h"
#include <sstream>

// cpp main loop
int main(int argc, char \*\*argv)
{
// create a node with the name of "talker"
ros::init(argc, argv, "talker");

// creat a class for calling node (n)
ros::NodeHandle n;

// create a publisher-topic with the name of chatter (the topic name is chatter)
ros::Publisher chatter_pub = n.advertise<std_msgs::String>("chatter", 1000); // 1000 msg available
ros::Rate loop_rate(10); // 100ms delay

int count = 0;
while (ros::ok()) // when roscore is ok!
{

    // create msg and add it to class
    std_msgs::String msg;
    std::stringstream ss;

    // print hello world as msg
    ss << "hello world " << count;

    // log the msg in terminal
    msg.data = ss.str();
    ROS_INFO("%s", msg.data.c_str());

    // publishing the created msg
    chatter_pub.publish(msg);

    // re-match with roscore
    ros::spinOnce();
    loop_rate.sleep(); // 100ms delay
    ++count;

}

return 0;
}
```

برای مشاهده این مثال در داکیومت راس به لینک زیر مراجعه نمایید:

http://wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber%28c%2B%2B%29

حال که برنامه فرستنده یا همان پابلیشر (talker.cpp) ایجاد شد به سراغ ایجاد برنامه دریافت کنند یا همان سابسکرایبر (listener.cpp) می رویم. با کمک کامند زیر آنرا ایجاد کنید:

```bash
$ touch listener.cpp
```

و سپس درون آن کدهای زیر را قرار دهید:

```c++
// libs
#include "ros/ros.h"
#include "std_msgs/String.h"

// call-back function for receive data
void chatterCallback(const std_msgs::String::ConstPtr& msg) // Input: String
{
  ROS_INFO("I heard: [%s]", msg->data.c_str()); // log received data in terminal
}


int main(int argc, char **argv)
{

  // create a node with the name of "listener"
  ros::init(argc, argv, "listener");
  ros::NodeHandle n;

  // create a subscriber-topic with the name of chatter (the topic name is chatter)
  ros::Subscriber sub = n.subscribe("chatter", 1000, chatterCallback); // listen to topic with name of chatter
  ros::spin(); // re-match with ros core

  return 0;
}
```

حال برای کامپایل کردن ابتدا باید تغییرات لازم را در فایل CMakeList ایجاد کنیم. باید دو فایل talker.cpp و listener.cpp را به عنوان دو فایلی که قرار است کامپایل شوند معرفی کنیم. دو کد زیر را در بخش build قرار دهید:

```c
add_executable(talker src/talker.cpp)
target_link_libraries(talker ${catkin_LIBRARIES})
add_dependencies(talker beginner_tutorials_generate_messages_cpp)

add_executable(listener src/listener.cpp)
target_link_libraries(listener ${catkin_LIBRARIES})
add_dependencies(listener beginner_tutorials_generate_messages_cpp)
```

البته تفاوتی نمی کند کجا فایل قرار گرفته باشد 😂

توجه کنید اگر از ورژن ملودیک و نئوتیک راس استفاده میکنید دو خط زیر را قرار دهید:

```c
add_executable(talker src/talker.cpp)
target_link_libraries(talker ${catkin_LIBRARIES})


add_executable(listener src/listener.cpp)
target_link_libraries(listener ${catkin_LIBRARIES})
```

حال به شاخه اصلی بروید و با catkin_make برنامه را کامپایل نمایید و با کمک دستور rosrun نود های نوشته شده را اجرا نمایید:

```bash
$ cd ..
$ catkin_make
$ roscore
$ rosrun beginner_tuts listener
$ rosrun beginner_tuts talker
```

اکنون اجرا شدن برنامه را مشاهده خواهید کرد، فراموش نکته هسته راس را روشن نمایید. همچنین اگر در کد سی پلاس پلاس تغییری کردید مجدد کامپلایل نمایید (با کنترل اس، تغییرات اعمال نمیشه 😂) برای مشاهده جزئیات بیشتر می توانید به لینک زیر در داکیومنت خود راس مراجعه نمایید:

http://wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber%28c%2B%2B%29

ایجاد همین پابلیشر سابسکرایبر در پایتون بسیار راحت تر می باشد، چراکه نیاز به کامپایل ندارد و برنامه های پایتون به صورت آنلاین (چون مفسریند) اجرا می شود. یک پوشه تحت عنوان scripts در دایرکتوری اصلی پکیج beginner_tuts ایجاد کنید و دو فایل پایتونی با نام های talker.py و listener.py ایجاد کنید:

```bash
$ roscd beginner_tuts
$ mkdir scripts
$ cd scripts
$ touch talker.py listener.py
```

اکنون کد زیر را در فایل talker.py قرار دهید:

```python
#!/usr/bin/env python
import rospy
from std_msgs.msg import String

def talker(): # create a node with name of talker
rospy.init_node('talker', anonymous=True)

    # create a topic (publisher) with name of chatter
    pub = rospy.Publisher('chatter', String, queue_size=10)
    rate = rospy.Rate(10) # 10hz or 100ms
    while not rospy.is_shutdown(): # until when roscore is ok
        hello_str = "hello world %s" % rospy.get_time() # make an string
        rospy.loginfo(hello_str) # log it in terminal
        pub.publish(hello_str) # publish it in chatter topic
        rate.sleep() # 100ms delay

if **name** == '**main**': # run it if we are in this file
try:
talker()
except rospy.ROSInterruptException: # any error then pass it
pass
```

و کد زیر را نیز در listener.py قرار دهید:

```python
#!/usr/bin/env python
import rospy
from std_msgs.msg import String

# call-back function

def callback(data):
rospy.loginfo(rospy.get_caller_id() + 'I heard %s', data.data)

def listener(): # create a node with name of listener
rospy.init_node('listener', anonymous=True)

    # create a topic (subscriber) with name of chatter
    rospy.Subscriber('chatter', String, callback)

    rospy.spin() # re-match with roscore

if **name** == '**main**':
listener()
```

برای اجرای کدهای پایتون باید دسترسی آنها را با کمک کامند chmod تغییر بدهیم، کافیست در پوشه script یک دور کامند زیر را اجرا نماییم (همه برنامه ها قابل اجرا می شوند):

```bash
$ roscd beginner_tuts
$ cd scripts
$ chmod +x *
```

حال با کمک کامندهای زیر می توانید این مثال را اجرا نمایید:

```bash
$ roscore
$ rosrun beginner_tuts talker.py
$ rosrun beginner_tuts listener.py
```

توجه شود که اگر با خطا روبرو شدید کامندهای زیر را نیز امتحان کنید (روی برخی از لینوکس ها با python و روی برخی دگر با python3)

```bash
$ roscore
$ python3 talker.py
$ python3 listner.py
```

توجه شود که اگر از در داخل ROS ملودیک هستید در برنامه های پایتونی خود از کامنت هدر زیر استفاده کنید:

```python
#!/usr/bin/env python
```

و اگر در داخل نئوتیک هستید از کد زیر استفاده کنید:

```python
#!/usr/bin/env python3
```

با این کامنت ورژن پایتون سند پایتونی را به مفسر پایتون می فهمانید.

## آشنا با پیام ها و سرویس ها

در برخی از مواقع نیاز می شود تا فرمت خاصی برای ارتباط از نوع تاپیک تعریف کنیم. در این مواقع از پیام ها (Message) استفاده می کنیم. ساختار یک پیام را می توان با کمک دیتا-تایپ های زیر تعریف کرد:

```
int8 (also uint8)
int16
int32
int64
float32
string
time
duration
(other types of msg)
(using arrays [])
header
```

برای ایجاد یک مسیج اختصاصی (برای مثال مسیج Student) در ابتدا نیاز است تا ابتدا در داخل پوشه پکیج مان یک پوشه به نام msg ایجاد کنیم و سپس در داخل این پوشه، یک فایل با نام مسیج مورد نظر (مثلا Student.msg) ایجاد نماییم:

```bash
$ roscd beginner_tuts
$ mkdir msg && cd msg
$ touch Student.msg
```

سپس در فایل Student.msg ساختار پیام خود را با کمک دیتاتایپ هایی که مشخص شد تعریف کنیم (برای مثال نام و نام خانوادگی را با رشته، سن را عدد اینتجر و نمرده را با float32 مشخص می کنیم):

```
string name
string lastname
int8 age
float32 score
```

حال که مسیج را تعریف کردیم نیاز است تا آنرا به راس و کامپایلر بشناسانیم. درون پوشه پکیج در داخل فایل package.xml دو خط زیر را uncomment کنید:

```xml
<build_depend>message_generation</build_depend>
<exec_depend>message_runtime</exec_depend>
```

برای شناساندن این نوع پیام به کامپایلر نیاز است تا در فایل CMakeList.txt نیز تغییراتی اعمال کنیم. در ابتدا نیاز است تا پکیج message_generation را به لیست پکیج های پیش نیاز اضافه کنیم، یعنی در داخل تابع find_package قرار دهیم، که در واقع این تابع به صورت زیر در می آید:

```c++
find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  message_generation
)
```

همچنین نیاز است تا خط زیر در داخل تابع catkin_package کامنتش غیرفعال و message_runtime به انتهای آن اضافه شود:

```c++
catkin_package(
  CATKIN_DEPENDS roscpp rospy std_msgs message_runtime
)
```

حال نیاز است تا آدرس فایل مسیج را به تابع add_message_file بدهیم (حتما Uncomment کنید و در همان محل قرار دهید):

```c++
 add_message_files(
   FILES
   Student.msg
 )
```

همچنین بخش generate_message را نیز به حالت uncomment در بیاورید:

```c++
 generate_messages(
   DEPENDENCIES
   std_msgs
 )
```

اکنون مجدد به شاخه اصلی پروژه بروید و یک دوره catkin_make را اجرا کنید. سپس اگر محیط کار را سورس نکردید، سورس کنید (اگر هم که کردید که هیچ) . اکنون با کمک دستور زیر می توانید مسیج ایجاد شده را مشاهده نمایید:

```bash
$ rosmsg show Student
```

برای مشاهده جزئیات بیشتر در مورد پیام ها (Messages) می توانید به لینک زیر در داخل خود ویکی راس مراجعت نمایید:

http://wiki.ros.org/ROS/Tutorials/CreatingMsgAndSrv

در ادامه به سراغ سرویس ها می رویم. سرویس یک نوع ارتباطی دو طرفه می باشد، شبیه توابع در برنامه نویسی است. برخی از کامندهایی که در کار با سروریس ها بکار می آیند را با هم مرور می کنیم. لیستی از این کامندها

```bash
$ rosservice -h
$ rosservice list
$ rosservice type /clear
$ rosservice info /clear
```

برای استفاده از یک سرویس در درون ترمینال از سوئیچر call استفاده می کنیم، برای مثال قصد داریم از سرویس /clear که مربوط به پکیج turtlesim است استفاده کنیم. در درون این سرویس یک تابع قرار گرفته که مسیری که لاکپشت رفته را پاک میکند (توجه کنید که این سرویس در ورودی چیزی نمی گیرد):

```bash
$ rosservice call /[service-name] [value]
$ rosservice call /clear
```

برای مشاهده نوع مسیج هایی که در سرویس ها رد بدل می شود از کامند زیر استفاده می کنیم:

```bash
$ rossrv show turtlesim/Spawn

```

توجه شود که مقدار turtlesim/Spawn در کامند بالا با کمک rosservice type استخراج شده است. با کمک کامند بالا ما ساختار این مسیج را می بینیم! برای راحتی می توانیم با کمک دستور پایپ (|) دو دستور را در یک کامند لاین اجرا کنیم. دستور پایپ خروجی دستور اول را در ورودی دستور دوم قرار می دهد:

```bash
$ rosservice type /spawn | rossrv show
```

در ادامه می خواهیم در پنچره یک لاکپشت دیگر با کمک سرویس spawn ایجاد کنیم. ساختار دستوری زیر را اجرا می کنیم:

```bash
$ rosservice call /[service-name] [datas]
$ rosservice call /spawn "x: -1.0 y: 1.0 theta: 2.0 name: 'myturtle'"
```

توجه کنید که با دوبار تب زدن می توانید ساختار دیتا را لود کنید! توجه کنید که سرویس spawn به ما به عنوان خروجی نام انتخابی را بازخواهد گرداند!

در ادامه به نحوه ایجاد یک سرویس در داخل پکیج مان می پردازیم. برای اینکار نیاز است تا ابتدا به دایرکتوری پروژه ما برویم و نیاز است در داخل پکیج مان پیام های مخصوص سرویس ها (که با فرمت .srv هستند) را ایجاد کنیم. بدین منظور ابتدا یک پوشه به نام srv که حاوی پیام های سرویسی ما هست را اجرا ایجاد می کنم و در داخل آن یک فایل با نام دلخواه و فرمت .srv (مثلا AddTwoInts.srv) را ایجاد میکنیم:

```bash
$ roscd beginner_tuts/
$ mkdir srv && cd srv
$ touch AddTwoInts.srv
```

در ادامه باید مسیج سرویسی را ایجاد کنیم (فرمت مشابه همان مسیج های عادی است با این تفاوت که در اینجا باید نوع خروجی را نیز مشخص کنیم، برای مشخص کردن خروجی از "---" استفاده میکنم:

```
int64 a
int64 b
---
int64 sum
```

همچنین از آنجایی که ما داریم از پکیج آموزشی خود را استفاده می کنیم می توانید مستقیمن این فایل را به پوشه srv کپی کنید. برای کپی کردن فایل های داخلی خود پکیج راس از دستور roscp استفاده میکنم:

```bash
$ roscd rospy_tutorials AddTwoInts.srv srv/AddTwoInts.srv
```

در ادامه برای فهماندن این نوع مسیج به کامپایلر از در داخل فایل CmakeLists.txt در بخش سرویس، تابع add_service_files را از حالت کامنت خارج و نام فایل srv مان را معرفی میکنم:

```python
## Generate services in the 'srv' folder
 add_service_files(
   FILES
   AddTwoInts.srv
 )
```

در ادامه با کمک دستور catkin_make یک دور از پکیج کامپایل می گیریم. اکنون ما سرویس را ایجاد کردیم (در واقع سرویس یک نوع مسیج است) و اکنون برای بهره گیری از این سرویس نیاز به یک سرور و کلاینت داریم. برای ایجاد سرور و کلاینت می توانیم از پاتیون یا سی پلاس پلاس بهره گیری کنیم. ابتدا ما با کمک سی پلاس پلاس این کار را انجام می دهیم.

برای ایجاد برنامه سی پلاس پلاس ما دو نود نیاز داریم یک نود که وظیفه سرور را برای ما انجام دهد و یک نود که برای ما وظیفه کلاینت را بر عهده بگیرد. ما دو فایل add_two_ints_client.cpp و add_two_ints_server.cpp را در داخل پوشه src ایجاد می کنیم. کد فایل add_two_ints_server.cpp به شرح زیر می باشد (کامنت ها گویای کد است):

```c++
#include "ros/ros.h"
#include "beginner_tuts/AddTwoInts.h"


// Service Servicer Function: add
bool add(beginner_tuts::AddTwoInts::Request  &req,
         beginner_tuts::AddTwoInts::Response &res)
{
  res.sum = req.a + req.b; // res = {sum}, req ={a,b}
  ROS_INFO("request: x=%ld, y=%ld", (long int)req.a, (long int)req.b);
  ROS_INFO("sending back response: [%ld]", (long int)res.sum);
  return true;
}


int main(int argc, char **argv)
{
  // Initiazte Node
  ros::init(argc, argv, "add_two_ints_server");
  ros::NodeHandle n;


  // Initiate Creating Service Server & And Publishing A "add" Service
  ros::ServiceServer service = n.advertiseService("add_two_ints", add);
  ROS_INFO("Ready to add two ints.");
  ros::spin();


  return 0;
}
```

و کد فایل add_two_ints_client.cpp حاوی کد زیر می باشد:

```c++
#include "ros/ros.h"
#include "beginner_tuts/AddTwoInts.h"
#include <cstdlib>


int main(int argc, char **argv)
{

  // Create A Node
  ros::init(argc, argv, "add_two_ints_client");
  if (argc != 3) // 3 Arguments in Terminal
  {
    ROS_INFO("usage: add_two_ints_client X Y");
    return 1;
  }


  // Create A Service Client
  ros::NodeHandle n;
  ros::ServiceClient client = n.serviceClient<beginner_tuts::AddTwoInts>("add_two_ints");

  // Create A Service
  beginner_tuts::AddTwoInts srv;


  // Getting Service a,b From Terminal Argument
  srv.request.a = atoll(argv[1]);
  srv.request.b = atoll(argv[2]);
  if (client.call(srv))
  {
    ROS_INFO("Sum: %ld", (long int)srv.response.sum);
  }
  else
  {
    ROS_ERROR("Failed to call service add_two_ints");
    return 1;
  }


  return 0;
}
```

پس از تنظیم کدها یک دور catkin_make را اجرا کنید تا فایل ها کامپایل شود. توجه کنید که حتما چهار خط زیر را در فایل CMakeList.txt قرار دهید تا این فایل ها به کامپایلر معرفی شوند:

```c++
add_executable(add_two_ints_server src/add_two_ints_server.cpp)
target_link_libraries(add_two_ints_server ${catkin_LIBRARIES})


add_executable(add_two_ints_client src/add_two_ints_client.cpp)
target_link_libraries(add_two_ints_client ${catkin_LIBRARIES})
```

در ادامه برای اجرای این کد، کامند های زیر را اجرا می کنیم:

```bash
$ roscore
$ rosrun beginner_tuts add_two_ints_serve
$ rosservice call /add_two_ints 1 2
$ rosrun beginner_tuts add_two_ints_client 2 3
```

در ادامه به نحوه ایجاد این برنامه در پایتون می پردازیم.

برای پایتون هم به صورت مشابه دو نود با نام های add_two_ints_client.py و add_two_ints_server.py ایجاد می کنیم. کد موجود در add_two_ints_server.py به شرح زیر است:

```python
#!/usr/bin/env python


from __future__ import print_function


from beginner_tuts.srv import AddTwoInts,AddTwoIntsResponse
import rospy


def handle_add_two_ints(req):
    print("Returning [%s + %s = %s]"%(req.a, req.b, (req.a + req.b)))
    return AddTwoIntsResponse(req.a + req.b)


def add_two_ints_server():
    rospy.init_node('add_two_ints_server')
    s = rospy.Service('add_two_ints', AddTwoInts, handle_add_two_ints)
    print("Ready to add two ints.")
    rospy.spin()


if __name__ == "__main__":
    add_two_ints_server()

```

کد موجود در add_two_ints_client.py به شرح زیر است:

```python
#!/usr/bin/env python

from **future** import print_function

import sys
import rospy
from beginner_tutorials.srv import \*

def add_two_ints_client(x, y):
rospy.wait_for_service('add_two_ints')
try:
add_two_ints = rospy.ServiceProxy('add_two_ints', AddTwoInts)
resp1 = add_two_ints(x, y)
return resp1.sum
except rospy.ServiceException as e:
print("Service call failed: %s"%e)

def usage():
return "%s [x y]"%sys.argv[0]

if **name** == "**main**":
if len(sys.argv) == 3:
x = int(sys.argv[1])
y = int(sys.argv[2])
else:
print(usage())
sys.exit(1)
print("Requesting %s+%s"%(x, y))
print("%s + %s = %s"%(x, y, add_two_ints_client(x, y)))
```

## آشنایی با پارامترها

در ادامه به روش ارتباطی پارامتری می پردازیم. پارامترها ثابت هایی هستند که در هسته راس ذخیره می شوند. با کمک دستور زیر می توانیم با پارامترها کار کنیم:

```bash
$ rosparam -h
$ rosparam set
$ rosparam get
$ rosparam delete
$ rosparam list
```

برای خواندن یا ذخیره کردن پارامترها داخل یک فایل از دو کامند زیر بهره می بریم:

```bash
$ rosparam load [file-address]
$ rosparam dump [file-address]
```

برای استفاده از پارامترها در برنامه سی پلاس پلاس به شیوه زیر عمل می کنیم:

```c++
ros::NodeHandle nh;
std::string global_name, relative_name, default_param;
if (nh.getParam("/global_name", global_name))
{
  ...
}

if (nh.getParam("relative_name", relative_name))
{
...
}

// Default value version
nh.param<std::string>("default_param", default_param, "default_value");
```

همچنین بدون ایجاد نود هم می توانید به طریق زیر عمل کنید:

```c++
std::string global_name, relative_name, default_param;
if (ros::param::get("/global_name", global_name))
{
  ...
}

if (ros::param::get("relative_name", relative_name))
{
...
}

// Default value version
ros::param::param<std::string>("default_param", default_param, "default_value");
```

برای ست کردن مقادیر بر روی پارامتر در سی پلاس پلاس به شیوه زیر عمل می کنیم:

```c++
ros::NodeHandle nh;
nh.setParam("/global_param", 5);
nh.setParam("relative_param", "my_string");
nh.setParam("bool_param", false);
```

همچنین بدون ایجاد نود می توانید پارامترها مقدار دهی کنید:

```c++
ros::param::set("/global_param", 5);
ros::param::set("relative_param", "my_string");
ros::param::set("bool_param", false);
```

برای مشاهده موجود بودن یک پارامتر می توانید به دو روش زیر عمل کنید:

```c++
ros::NodeHandle nh;
if (nh.hasParam("my_param"))
{
  ...
}
```

یا

```c++
if (ros::param::has("my_param"))
{
  ...
}
```

همچنین برای پاک کردن یک پارامتر در سی پلاس پلاس می توانید به روش زیر عمل کنید:

```c++
ros::NodeHandle nh;
nh.deleteParam("my_param");
```

یا

```c++
ros::param::del("my_param");
```

در زبان پایتون نیز مشابه و ساده تر می باشد:

دریافت اطلاعات یک پارامتر:

```python
global_name = rospy.get_param("/global_name")
relative_name = rospy.get_param("relative_name")
private_param = rospy.get_param('~private_name')
default_param = rospy.get_param('default_param', 'default_value')

# fetch a group (dictionary) of parameters
gains = rospy.get_param('gains')
p, i, d = gains['p'], gains['i'], gains['d']
```

مقداردهی پارامترها:

```python
# Using rospy and raw python objects
rospy.set_param('a_string', 'baz')
rospy.set_param('~private_int', 2)
rospy.set_param('list_of_floats', [1., 2., 3., 4.])
rospy.set_param('bool_True', True)
rospy.set_param('gains', {'p': 1, 'i': 2, 'd': 3})

# Using rosparam and yaml strings
rosparam.set_param('a_string', 'baz')
rosparam.set_param('~private_int', '2')
rosparam.set_param('list_of_floats', "[1., 2., 3., 4.]")
rosparam.set_param('bool_True', "true")
rosparam.set_param('gains', "{'p': 1, 'i': 2, 'd': 3}")

rospy.get_param('gains/p') #should return 1
```

مشاهده موجود بودن یک پارامتر و حذف آن:

```python
if rospy.has_param('to_delete'):
    rospy.delete_param('to_delete')
```

برای مشاهده جزئیات بیشتر به لینک های زیر مراجعه نمایید:

پایتون: http://wiki.ros.org/rospy/Overview/Parameter%20Server

سی پلاس پلاس: http://wiki.ros.org/roscpp/Overview/Parameter%20Server

توجه شود که پارامترها برای تنظیمات استفاده میشه!

## آشنایی با rosbag

هنگامی که نیاز باشد پیام های داخل یک یا چند تاپیک را ضبط کنیم، از rosbag بهره می بریم. برای ایجاد فایل بگ خوب است که یک دایرکتوری در پوشه فضای کاری مان ایجاد میکنم و فایل های بگ را در داخل آن ذخیره سازی می کنیم. برای ذخیره کردن پیام های داخل تمام تاپیک ها از دستور زیر بهره می بریم:

```bash
$ mkdir rosbag
$ cd rosbag
$ rosbag record -a
```

برای پایان دادن به ضبط از دستور control+c استفاده می کنیم. برای مشاهده فایل بگ ایجاد شده و مشاهده جزیئات آن (مخل ذخیره، ورژن، طول زمانی، زمان استارت و پایان، حجم، نوع مسیج ها، تاپیک ها، تعداد پیام های ضبط شده و ...) از دستور زیر می توان استفاده کرد:

```bash
$ ls
$ rosbag info [bag-name]
```

اکنون برای اجرا کردن فایل بگ از دستور play استفاده می کنیم. در مثال ویدیو از ماژول turtle برای اجرای تست rosbag استفاده شده بود، ما برای تست نود teleop_key را می بندیم و همچنین تاپیک cmd_vel را اکو می کنیم و سپس فایل بگ را play می کنیم:

```bash
$ rostopic echo /turtle1/cmd_vel
$ rosbag play [bag-name]
```

مشاهده خواهد شد که تاپیک های ضبط شده منتشر شده و لاکپشت حرکت می کند. برای puase/play کردن می توان از دکمه space بهره برد. با کلید s هم می توانیم فریم به فریم بگ را اجرا کنیم. همچنین با سوئیچر -r می توانیم سرعت پلی شدن را افزایش یا کاهش دهیم. برای مثال می خواهیم با سرعت 2 برابر پخش شود:

```bash
$ rosbag play [bag-name] -r 2
```

برای رکورد کردن یک تاپیک خاص می توان از دستور زیر بهره برد (همچنین یک نام می توان به بگ اختصاص داد):

```bash
$ rosbag record [topic1] [topic2] -O [bag-name]
```

برای مشاهده جزئیات بیشتر در مورد rosbag می توانید به لینک های زیر در داکیومنت راس مراجعه نمایید:

http://wiki.ros.org/ROS/Tutorials/Recording%20and%20playing%20back%20data

http://wiki.ros.org/ROS/Tutorials/reading%20msgs%20from%20a%20bag%20file

## آشنایی با roswtf

ابزار بعدی roswtf هست که خیلی کم استفاده می شود. داخل هر دایرکتوری وارد کنید اطلاعات مفیدی برای دیباگ کردن می دهد. برای مشاهده جزئیات بیشتر به لینک زیر مراجعه نمایید:

http://wiki.ros.org/ROS/Tutorials/Getting%20started%20with%20roswtf

## آشنایی با ابزارهای rqt

در ادامه به برسی ابزارهای rqt می پردازیم. ابزار زیر نمودار نودها و تاپیک ها را به صورت گرافیکی به ما نمایش می دهد:

```bash
$ rosrun rqt_graph rqt_graph
```

خروجی این دستور به شکل زیر می باشد:

![Alt text](image-5.png)

دستور زیر به ما پیام های رد بدل شده بین نودها را در داخل کنسول زیبا نمایش میدهد، همچنین امکان فیلترینگ دیتا نیز هست:

```bash
$ rosrun rqt_console rqt_console
```

خروجی این دستور به شکل زیر خواهد بود:

![Alt text](image-6.png)

توجه شود که سطح اهمیت پیام ها به شرح زیر است:

```
debug
info
warning
error
fatal
```

که برای Api مربوط به rospy استفاده از این لاگ ها به شرح زیر می شود:

```python
rospy.logdebug(msg, *args, \*\*kwargs)
rospy.loginfo(msg, *args, **kwargs)
rospy.logwarn(msg, \*args, **kwargs)
rospy.logerr(msg, *args, \*\*kwargs)
rospy.logfatal(msg, *args, \*\*kwargs)
```

توجه شود که اگر نیاز شد از متغیری را در پیام لاگ ها چاپ کنید از فرمت زیر بهره ببرید:

```python
rospy.logerr("%s returned the invalid value %s", other_name, other_value)
```

همچنین اگر نیاز شد متغیر صحیح و فلوت لاگ شود از فرمت زیر می توانید بهره ببرید:

```python
rospy.logerr("This is a integer %d num and this is float %f", 23, 23.232)
```

برای مشاهده جزئیات بیشتر به لینک زیر مراجعه نمایید:

آشنایی با ابزارهای rqt:
http://wiki.ros.org/ROS/Tutorials/UsingRqtconsoleRoslaunch

لاگ های درپایتون: http://wiki.ros.org/rospy/Overview/Logging

لاگ ها در سی پلاس پلاس: http://wiki.ros.org/roscpp/Overview/Logging

## واحد های استاندارد

واحدهای استاندارد ROS به شرح زیر هست:

- طول و فاصله: متر
- جرم: کیلوگرم
- زمان: ثانیه
- جریان: آمپر
- اختلاف پتانسیل: ولت
- مغناطیس: تسلا
- زاویه: رادیان
- فرکانس: هرتز
- نیرو: وات
- دما: سلسیوس

بقیه واحد ها مثل سرعت و شتاب و ... از تقسیم واحد های بالا بر هم بدست می آیند.

## آشنایی با فایل های launch

در ادامه به لانچ فایل های می پردازیم که به ما این امکان را می دهند که با اجرای یک فایل، چندین نود را همزمان درون یک ترمنیال اجرا کنیم که خیلی به خلوت شدن محیط کاری کمک می کند. برای اینکار یک پوشه مجزا در پکیج مان تحت عنوان launch ایجاد می کنیم و فایل های launch مان را در داخل این پوشه قرار می دهیم:

```bash
$ roscd beginner_tuts/
$ mkdir launch
```

حال مثال می خواهیم برنامه لاکپشت را به کمک یک لانچ فایل اجرا کنیم. یک فایل با نام turtle_run.launch ایجاد می کنیم:

```bash
$ touch turtle_run.launch
```

و کد زیر را در داخل آن قرار می دهیم:

```xml
<launch>
    <node pkg="turtlesim" type="turtlesim_node" name="sim" />
    <node pkg="turtlesim" type="turtle_teleop_key" name="control" />
</launch>
```

در کد بالا 2 نود turtlesim_node و turtle_teleop_key از پکیج turtlesim قرار است اجرا شود. (توجه شود که type همان نود است) و یک نام هم به هر کدام از نود ها اختصاص می دهیم. توجه شود که قبل از اجرا کردن یک فایل launch حتما باید هسته فعال باشد ولی اگر هم فعال نبود، خود دستور roslaunch آنرا اجرا می کند. با دستور زیر می توانیم فایل لانچ ایجاد شده را اجرا کنیم:

```bash
$ roslaunch turtle_run.launch
```

همچنین توجه شود که ما می توانیم با کمک دستور زیر از سایر دایرکتوری ها فایل لانچ موجود در پکیج مدنظر را اجرا کنیم:

```bash
$ roslaunch beginner_tuts turtle_run.launch
```

درون فایل لانچ می توان از attribute ها مختلف بهره برد. یکی از این attribute ها respawn می باشد که نود را هر چند بار هم که ببندیم مجدد اجرا کند (در این مثال پنجره لاکپشت پس از هر بار بسته شدن، مجدد پس از 3 ثانیه تاخیر از نو اجرا می شود. توجه شود که تاخیر اتریبیوت اجباری نیست!)

```xml
<launch>
    <node pkg="turtlesim" type="turtlesim_node" name="sim" respawn="true" respawn_deley="3"/>
    <node pkg="turtlesim" type="turtle_teleop_key" name="control" />
</launch>
```

یا می توانیم با کمک اتریبیوت required یک نود را اجباری کنیم (در صورتیکه این نود بسته شود، کل هسته متوقف می شود.):

```xml
<launch>
    <node pkg="turtlesim" type="turtlesim_node" name="sim" required="true" />
    <node pkg="turtlesim" type="turtle_teleop_key" name="control" />
</launch>
```

یا می توانیم در صورتی که نود آرگومان ورودی دارد، برای آن مقادیری را نیز تعیین کنیم:

```xml
<launch>
    <node pkg="turtlesim" type="turtlesim_node" name="sim" args="1 2 3" />
    <node pkg="turtlesim" type="turtle_teleop_key" name="control" />
</launch>
```

یا می توانیم بگوییم در صورتیکه که یک نود اجرا شد، تمام پارامترهای قبلی ذخیره شده در رم حذف شود:

```xml
<launch>
    <node pkg="turtlesim" type="turtlesim_node" name="sim" clear_params="true" />
    <node pkg="turtlesim" type="turtle_teleop_key" name="control" />
</launch>
```

توجه شود که در زبان xml تگ هایی که تگ ها بسته شونده و تکی به شکلی زیر است:

```xml
<closing></closing>
<non-closing>
```

تگ node را می توانیم به صورت دوتایی نیز تعریف کنیم و در داخل آن از تگهای مختلف استفاده کنیم از جمله تگ env که برای تعریف مجدد متغیرهای محیط کاری تعریف می شود، مقدار name نام آن متغیر و مقدار value برابر مقدار جدیدی است که می خواهیم به آن اختصاص دهیم:

```xml
<launch>
    <node pkg="turtlesim" type="turtlesim_node" name="sim">
        <env name="Env_Varaible_Name" value="New_Value" />
    </node>
    <node pkg="turtlesim" type="turtle_teleop_key" name="control" />
</launch>
```

همچنین می توان تاپیک ها را re-map کرد (یعنی یک نام دیگر بجای نام پیشفرض تاپیک کنیم، این مورد زمانی کاربردی می شود که نیاز باشد از یک نود و تاپیک چندین بار استفاده کنیم و می خواهیم تاپیک هر نود مجزا باشد). برای مثال در مثال لاکپشت می خواهیم که تاپیک cmd_vel با نام vel2 ریمپ شود، در محیط ترمینال این ریمپ کردن به شکل زیر در می آید:

```bash
$ roscore
$ rosrun turtlesim turtlesim_node /turtle1/cmd_vel:=vel2
$ rosrun turtlesim turtle_teleop_key /turtle1/cmd_vel:=vel2
```

و در محیط لانچ فایل مثال لاکپشت به صورت زیر در می آید:

```xml
<launch>
    <node pkg="turtlesim" type="turtlesim_node" name="sim">
        <remap from="/turtle1/cmd_vel" to="vel2" />
    </node>
    <node pkg="turtlesim" type="turtle_teleop_key" name="control">
        <remap from="/turtle1/cmd_vel" to="vel2" />
    </node>
</launch>
```

همچنین می توانیم در تگ نود یک پارامتر دلخواه را تعریف کنیم تا در هنگام اجرای هسته، در فضای پارامترها اجرا شود (توجه شود نوع پارامتر می تواند str ، int ، bool ، float). در صورتیکه تعداد پارامترهای برنامه ما زیاد هست می توانیم آنرا در داخل یک فایل ذخیره کنیم و در داخل لانچ فایلمان آنرا فراخوانی کنیم. بهتر است که این فایل در یک پوشه مجزا به نام param ساخته شود:

```bash
$ roscd beginner_tuts
$ mkdir params
$ cd params/
$ touch param
```

در داخل فایل param مثلا متغیر زیر را ذخیره می کنیم:

```
hello world!
```

در ادامه در کد لانچ فایل:

```xml
<launch>
    <node pkg="turtlesim" type="turtlesim_node" name="sim">
        <remap from="/turtle1/cmd_vel" to="vel2" />
        <param name="fromFile" type="str" textfile="$(find beginner_tuts)/params/param" />

    </node>
    <node pkg="turtlesim" type="turtle_teleop_key" name="control">
        <remap from="/turtle1/cmd_vel" to="vel2" />
    </node>
</launch>
```

البته بهتر برای حالتی که قرار است تعداد زیادی پارامترا را اجرا کنیم، حتما از فرمت yaml بهره ببریم. برای اینکار یک پوشه yaml ایجاد می کنیم و پارامترهایمان را در داخل آن ذخیره کنیم:

```bash
$ roscd beginner_tuts/
$ mkdir yaml
$ cd yaml
$ touch param.yaml
```

در داخل فایل param.yaml می توانیم با کمک فرمت داده استاندارد Yaml پارامترهای مدنظرمان را تعریف کنیم، برای مثال:

```yaml
paramGroup1:
  intPAram: 1
  floatParam: 5.2323
paramGroup2:
  listParam: [1, 2, 3, "four"]
  dicParam:
    a: "This is a"
    b: "and this is b"
```

حال برای خواندن این فایل داخل لانچ فایل به ترتیب زیر عمل می کنیم:

```xml
<launch>
    <node pkg="turtlesim" type="turtlesim_node" name="sim">
        <remap from="/turtle1/cmd_vel" to="vel2" />
        <param name="fromFile" type="str" textfile="$(find beginner_tuts)/params/param" />
        <rosparam command="load" file="$(find beginner_tuts)/yaml/param.yaml" />

    </node>
    <node pkg="turtlesim" type="turtle_teleop_key" name="control">
        <remap from="/turtle1/cmd_vel" to="vel2" />
    </node>
</launch>
```

و برای اجرا همانند سابق عمل می کنیم:

```bash
$ roslaunch beginner_tuts turtle_run.launch
```

همچنین با کمک تگ rosparam نیز می توانیم متغیر خاصی در محیط مقدار دهی کنیم، به شکل زیر:

```xml
<launch>
    <node pkg="turtlesim" type="turtlesim_node" name="sim">
        <rosparam param="NN">1212</rosparam>
    </node>
    <node pkg="turtlesim" type="turtle_teleop_key" name="control">
        <remap from="/turtle1/cmd_vel" to="vel2" />
    </node>
</launch>
```

برای لانچ فایل ها نیز می توان آرگومان ورودی تعریف کرد، یعنی کاری کرد که هنگام اجرای یک لانچ فایل در ترمینال ورودی از آن بگیریم. در مثال زیر فایل لانچ یک آرگومان می گیرد و آنرا در متغیری به نام myArg ذخیره می کند که در جای جای فایل لانچ قابل استفاده است (می توان یک مقدار دیفالت نیز تعریف کرد):

```xml
<launch>
    <arg name="myArg" default="[2,3]" />

    <node pkg="turtlesim" type="turtlesim_node" name="sim">
        <remap from="/turtle1/cmd_vel" to="vel2" />
        <param name="fromFile" type="str" textfile="$(find beginner_tuts)/params/param" />
        <rosparam command="load" file="$(find beginner_tuts)/yaml/param.yaml" />
        <param name="NN" value="$(arg myArg)" />
    </node>
    <node pkg="turtlesim" type="turtle_teleop_key" name="control">
        <remap from="/turtle1/cmd_vel" to="vel2" />
    </node>

</launch>
```

همچنین در فایل های لانچ می توانیم یک فایل لانچ دیگر را فراخوانی و اینکلود کنیم:

```xml
<launch>
    <include file="$(find beginner_tuts)/launch/somefile.launch" />
    ...
</launch>
```

پس از اینکلود کردن، قبل از اجرای بدنه اصلی لانچ فایل، فایل اینکلود شده اجرا می شود. برای کامنت کردن در فایل xml از همان روش html بهره می بریم:

```xml
<!-- my comment -->
```

همچنین می توانیم یک فایل لانچ را با نیم اسپیس های گوناگون (ns) گروپ بندی کنیم (زیاد کاربردی نداره ولی بد نیست بدونیم):

```xml
<launch>
    <group ns="group1">
    <node pkg="turtlesim" type="turtlesim_node" name="sim">
        <remap from="/turtle1/cmd_vel" to="vel2" />
        <param name="fromFile" type="str" textfile="$(find beginner_tuts)/params/param" />
        <rosparam command="load" file="$(find beginner_tuts)/yaml/param." />

    </node>
    <node pkg="turtlesim" type="turtle_teleop_key" name="control">
        <remap from="/turtle1/cmd_vel" to="vel2" />
    </node>
    </group>

    <group ns="group2">
        .... other nodes ...
    </group>

</launch>
```

برای مشاهده جزئیات بیشتر به داکیومنت راس مراجعه نمایید:

http://wiki.ros.org/roslaunch

http://wiki.ros.org/ROS/Tutorials/UsingRqtconsoleRoslaunch
