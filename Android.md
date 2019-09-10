# 广播方式
 ## 1.LocalBroadcastManager 
Intent intent = new Intent();
intent.setAction("getLot");
LocalBroadcastManager.getInstance(getActivity()).sendBroadcast(intent);  

注：LocalBroadcastManager 无法和 PendingIntent 一起使用(原因：) 


# 计时方式
## 1.AlarmManager
AlarmManager alarmManager = (AlarmManager)getContext().getSystemService(ALARM_SERVICE);
alarmManager.setRepeating(AlarmManager.RTC_WAKEUP, System.currentTimeMillis(), 3000, pendingIntent);

## 2.Timer
Timer timer;
TimerTask task;

task = new TimerTask() {
        @Override
        public void run() {
            Log.i("@113","1111");
        }
    };
timer = new Timer();
timer.schedule(task, 0, 30000);   //第一个参数 ：调用任务， 第二个参数 ： 第一次调用延迟时间， 第三个参数 ： 循环调用间隔时间 。 时间单位 微秒
timer.cancal();

注：timer.cancel() 后再次调用 timer.cancal() 会报错，所以 timer 不能写成单例， 每次都需要 timer = new Timer()

# 调用Google Map
## 1.使用Google Map Url
Intent intent = new Intent(Intent.ACTION_VIEW,                
Uri.parse("https://www.google.com/maps/@22.5915296,113.5945795,8.04z")        );
intent.setClassName("com.google.android.apps.maps","com.google.android.maps.MapsActivity");
startActivity(intent);
