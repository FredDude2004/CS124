# Janaury 30th, 2024 Labs
## Lab 1
Complete the definitions of the Clock, AlarmClock, WorldClock, and WorldAlarmClock classes given below.

In the Clock class you only need to implement the tickTock() method.

In the AlarmClock class, be careful with the implementation of the alarm() method. The alarm is "on" for one hour. This is tricky if the alarm is set just after 12:00 because the alarm stays on to just after 1:00.

The WorldAlarmClock class is both a world clock and an alarm clock. But a class in Java cannot inherit from two classes. So the WorldAlarmClock class has to inherit either WorldClock of AlarmClock (but not both). The WorldAlarmClock class below inherits from WorldClock. That means that you have to copy and paste most of the AlarmClock implementation into the WorldAlarmClock class. This shows that you cannot always avoid duplicating some code.
<pre>
           Clock
          /     \
         /       \
 AlarmClock    WorldClock
                   |
                   |
               WorldAlarmClock
</pre>
You do not need to write any code that tests your classes. Your classes will be tested by the Tester.java program. The Tester.java program expects a single input integer between 1 and 5. The Tester.java program then runs one of its five built in test cases.
### Clock
```java
/*
           Clock
          /     \
         /       \
 AlarmClock    WorldClock
                    |
                    |
               WorldAlarmClock
*/
class Clock
{
   private int hour;    // 1 <= hour <= 12
   private int minute;  // 0 <= minute <= 59

   /**
      Create a Clock object with the given time.

      @param hour    must be between 1 and 12
      @param minute  must be between 0 and 59
      @throws IllegalArgumentException when hour is not between 1 and 12
      @throws IllegalArgumentException when minute is not between 0 and 59
   */
   public Clock(int hour, int minute)
   {
      if (hour < 1 || 12 < hour)
         throw new IllegalArgumentException("bad hour value");
      if (minute < 0 || 59 < minute)
         throw new IllegalArgumentException("bad minute value");

      this.hour = hour;
      this.minute = minute;
   }


   public int getHour()
   {
      return this.hour;
   }


   public int getMinute()
   {
      return this.minute;
   }


   /**
      @param hour  must be between 1 and 12
      @throws IllegalArgumentException when hour is not between 1 and 12
   */
   public void setHour(int hour)
   {
      if (hour < 1 || 12 < hour)
         throw new IllegalArgumentException("bad hour value");

      this.hour = hour;
   }


   /**
      @param minute  must be between 0 and 59
      @throws IllegalArgumentException when minute is not between 0 and 59
   */
   public void setMinute(int minute)
   {
      if (minute < 0 || 59 < minute)
         throw new IllegalArgumentException("bad minute value");

      this.minute = minute;
   }


   /**
      Advance the clock's time by one minute.
      This is a 12-hour clock.
   */
   public void tickTock()
   {
      this.minute++;
      if (this.minute == 60)
      {
         this.minute = 0;
         this.hour++;
         if (this.hour == 13)
         {
            this.hour = 1;
         }
      }
   }


   @Override
   public String toString()
   {
      String pad = "";
      if (minute < 10) pad = "0";
      return hour + ":" + pad + minute;
   }
}
```

### Alarm Clock
```java
/*
           Clock
          /     \
         /       \
 AlarmClock    WorldClock
                   |
                   |
               WorldAlarmClock
*/
class AlarmClock extends Clock
{
   private int alarmHour;
   private int alarmMinute;

   /**
      Create an AlarmClock object with the given times.

      @param hour    must be between 1 and 12
      @param minute  must be between 0 and 59
      @param alarmHour    must be between 1 and 12
      @param alarmMinute  must be between 0 and 59
      @throws IllegalArgumentException when hour is not between 1 and 12
      @throws IllegalArgumentException when minute is not between 0 and 59
      @throws IllegalArgumentException when alarmHour is not between 1 and 12
      @throws IllegalArgumentException when alarmMinute is not between 0 and 59
   */
   public AlarmClock(int hour, int minute, int alarmHour, int alarmMinute)
   {    
      super(hour, minute);
      if (alarmHour < 1 || 12 < alarmHour)
         throw new IllegalArgumentException("bad alarm hour value");
      if (alarmMinute < 0 || 59 < alarmMinute)
         throw new IllegalArgumentException("bad alarm minute value");

      this.alarmHour = alarmHour;
      this.alarmMinute = alarmMinute;
   }


   public int getAlarmHour()
   {
      return this.alarmHour;
   }


   public int getAlarmMinute()
   {
      return this.alarmMinute;
   }


   /**
      @param alarmHour    must be between 1 and 12
      @param alarmMinute  must be between 0 and 59
      @throws IllegalArgumentException when alarmHour is not between 1 and 12
      @throws IllegalArgumentException when alarmMinute is not between 0 and 59
   */
   public void setAlarm(int alarmHour, int alarmMinute )
   {
      if (alarmHour < 1 || 12 < alarmHour)
         throw new IllegalArgumentException("bad alarm hour value");
      if (alarmMinute < 0 || 59 < alarmMinute)
         throw new IllegalArgumentException("bad alarm minute value");

      this.alarmHour = alarmHour;
      this.alarmMinute = alarmMinute;
   }


   /**
      The alarm is "on" for up to one hour after the time it is set for.

      @return true if the clock's time is equal to, or up to one hour past, the alarm time.
   */
   public boolean alarm()
   {
      boolean on = false;
      int limit = this.alarmHour + 1;
      int hour = this.getHour();
      int minute = this.getMinute();
     
      if (limit > 12) {
         if (hour == 12 && minute >= this.alarmMinute)
         {
            on = true;
         }
         if (hour == 1 && minute <= this.alarmMinute)
         {
            on = true;
         }
      }
         
      if (limit > this.alarmHour) {
         if (hour == this.alarmHour && minute >= this.alarmMinute)
         {
            on = true;
         }
         if (hour == this.alarmHour+ 1 && minute <= this.alarmMinute)
         {
            on = true;
         }
      }
      return on;
   }


   @Override
   public String toString()
   {
      String time = super.toString();
      String alarmTime = "";
      if (this.alarmMinute < 10) alarmTime = "0";
      alarmTime = this.alarmHour + ":" + alarmTime + alarmMinute;
      return time + " (Alarm " + alarmTime + ")";
   }
}
```

### World Clock
```java
/*
           Clock
          /     \
         /       \
 AlarmClock    WorldClock
                   |
                   |
               WorldAlarmClock
*/
class WorldClock extends Clock
{
   private String city;
   private int difference;

   /**
      Create a WorldClock object with the given time.

      @param hour    must be between 1 and 12
      @param minute  must be between 0 and 59
      @param city    String name for the other city
      @param difference  how many hours ahead or behind
      @throws IllegalArgumentException when hour is not between 1 and 12
      @throws IllegalArgumentException when minute is not between 0 and 59
   */
   public WorldClock(int hour, int minute, String city, int difference)
   {
      super(hour, minute);
      this.city = city;
      this.difference = difference;
   }


   public String getCity()
   {
      return this.city;
   }


   public int getDifference()
   {
      return this.difference;
   }


   public void setCity(String city)
   {
      this.city = city;
   }


   public void setDifference(int difference)
   {
      this.difference = difference;
   }


   public String getWorldTime()
   {
      String pad = "";
      if (this.getMinute() < 10) pad = "0";
     
      int worldHour = this.getHour() + difference;
      if (worldHour > 12)
         worldHour %= 12;
      if (worldHour < 1)
         worldHour = 12 + worldHour;
         
      return this.city + " " + worldHour + ":" + pad + this.getMinute();
   }


   @Override
   public String toString()
   {
      String time = super.toString();
      time += " (" + this.getWorldTime() + ")";
      return time;
   }
}
```

### World Alarm Clock
```java
/*
           Clock
          /     \
         /       \
 AlarmClock    WorldClock
                   |
                   |
               WorldAlarmClock
*/
class WorldAlarmClock extends WorldClock
{
   private int alarmHour;
   private int alarmMinute;

   /**
      Create an AlarmClock object with the given times.

      @param hour    must be between 1 and 12
      @param minute  must be between 0 and 59
      @param city    String name for the other city
      @param difference  how many hours ahead or behind
      @param alarmHour    must be between 1 and 12
      @param alarmMinute  must be between 0 and 59
      @throws IllegalArgumentException when hour is not between 1 and 12
      @throws IllegalArgumentException when minute is not between 0 and 59
      @throws IllegalArgumentException when alarmHour is not between 1 and 12
      @throws IllegalArgumentException when alarmMinute is not between 0 and 59
   */
   public WorldAlarmClock(int hour, int minute,
                          String city, int difference,
                          int alarmHour, int alarmMinute)
   {
      super(hour, minute, city, difference);
      if (alarmHour < 1 || 12 < alarmHour)
         throw new IllegalArgumentException("bad alarm hour value");
      if (alarmMinute < 0 || 59 < alarmMinute)
         throw new IllegalArgumentException("bad alarm minute value");

      this.alarmHour = alarmHour;
      this.alarmMinute = alarmMinute;
   }


    public int getAlarmHour()
   {
      return this.alarmHour;
   }


   public int getAlarmMinute()
   {
      return this.alarmMinute;
   }


   /**
      @param alarmHour    must be between 1 and 12
      @param alarmMinute  must be between 0 and 59
      @throws IllegalArgumentException when alarmHour is not between 1 and 12
      @throws IllegalArgumentException when alarmMinute is not between 0 and 59
   */
   public void setAlarm(int alarmHour, int alarmMinute )
   {
      if (alarmHour < 1 || 12 < alarmHour)
         throw new IllegalArgumentException("bad alarm hour value");
      if (alarmMinute < 0 || 59 < alarmMinute)
         throw new IllegalArgumentException("bad alarm minute value");

      this.alarmHour = alarmHour;
      this.alarmMinute = alarmMinute;
   }


   /**
      The alarm is "on" for up to one hour after the time it is set for.

      @return true if the clock's time is equal to, or up to one hour past, the alarm time.
   */
   public boolean alarm()
   {
   boolean on = false;
      int limit = this.alarmHour + 1;
      int hour = this.getHour();
      int minute = this.getMinute();
     
      if (limit > 12) {
         if (hour == 12 && minute >= this.alarmMinute)
         {
            on = true;
         }
         if (hour == 1 && minute <= this.alarmMinute)
         {
            on = true;
         }
      }
         
      if (limit > this.alarmHour) {
         if (hour == this.alarmHour && minute >= this.alarmMinute)
         {
            on = true;
         }
         if (hour == this.alarmHour+ 1 && minute <= this.alarmMinute)
         {
            on = true;
         }
      }
      return on;
   }


   @Override
   public String toString()
   {
      String time = super.toString();
      String alarmTime = "";
      if (this.alarmMinute < 10) alarmTime = "0";
      alarmTime = this.alarmHour + ":" + alarmTime + alarmMinute;
      return time + " (Alarm " + alarmTime + ")";
   }
}
```