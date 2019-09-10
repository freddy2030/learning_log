#广播方式
 ##1.LocalBroadcastManager 
Intent intent = new Intent();
intent.setAction("getLot");
LocalBroadcastManager.getInstance(getActivity()).sendBroadcast(intent);  

注：LocalBroadcastManager 无法和 PendingIntent 一起使用(原因：) 


#计时方式
##1.AlarmManager
AlarmManager alarmManager = (AlarmManager)getContext().getSystemService(ALARM_SERVICE);
alarmManager.setRepeating(AlarmManager.RTC_WAKEUP, System.currentTimeMillis(), 3000, pendingIntent);