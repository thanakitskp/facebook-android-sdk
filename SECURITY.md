
/ **
 * ลิขสิทธิ์ (c) 2014- ปัจจุบัน, Facebook, Inc. สงวนลิขสิทธิ์
 * * * *
 * คุณได้รับใบอนุญาตปลอดค่าลิขสิทธิ์ทั่วโลกสำหรับการใช้งาน
 * คัดลอกแก้ไขและแจกจ่ายซอฟต์แวร์นี้ในซอร์สโค้ดหรือรูปแบบไบนารีเพื่อใช้งาน
 * เกี่ยวข้องกับบริการบนเว็บและ API ที่จัดทำโดย Facebook
 * * * *
 * เช่นเดียวกับซอฟต์แวร์ใด ๆ ที่รวมเข้ากับแพลตฟอร์ม Facebook การใช้งานของคุณ
 * ซอฟต์แวร์นี้อยู่ภายใต้หลักการและนโยบายของนักพัฒนา Facebook
* [http://developers.facebook.com/policy/] ประกาศเกี่ยวกับลิขสิทธิ์นี้จะเป็น
 * รวมอยู่ในสำเนาทั้งหมดหรือบางส่วนที่สำคัญของซอฟต์แวร์
 * * * *
 * ซอฟต์แวร์มีให้ "ตามสภาพ" โดยไม่มีการรับประกันใด ๆ
 * โดยนัยรวมถึง แต่ไม่ จำกัด เพียงการรับประกันของการค้าขายความเหมาะสม
* สำหรับวัตถุประสงค์เฉพาะและการไม่ผูกขาด ไม่ว่าในกรณีใดผู้เขียนหรือ
 * ผู้ถือลิขสิทธิ์ต้องรับผิดต่อการเรียกร้องค่าเสียหายใด ๆ หรือความรับผิดอื่น ๆ
 * ในการดำเนินการตามสัญญาสัญญาละเมิดลิขสิทธิ์หรืออื่น ๆ ที่เกิดขึ้นจากนอกหรือใน
 * การเชื่อมต่อกับซอฟต์แวร์หรือการใช้งานหรือการจัดการอื่น ๆ ในซอฟต์แวร์
 * /

แพ็คเกจ com.facebook.appevents ;

นำเข้า android.content.Context ;
นำเข้า android.os.Bundle ;
นำเข้า android.support.annotation.RestrictTo ;

นำเข้า com.facebook.AccessToken ;

นำเข้า java.math.BigDecimal ;
นำเข้า java.util.Currency ;
นำเข้า java.util.Map ;
นำเข้า java.util.concurrent.Executor ;

นำเข้า com.facebook.FacebookSdk ;
นำเข้า com.facebook.appevents.AppEventsLogger.FlushBehavior ;

/ **
 * com.facebook.appevents.InternalAppEventsLogger มีไว้สำหรับการใช้งานแพ็กเกจอื่น ๆ ภายใน
* Facebook SDK สำหรับ Android การใช้คลาสใด ๆ ในแพ็คเกจนี้คือ
 * ไม่รองรับและอาจถูกแก้ไขหรือลบโดยไม่มีการเตือนเมื่อใดก็ได้
 * /

@RestrictTo ( RestrictTo . Scope . LIBRARY_GROUP )
ประชาชน ระดับ InternalAppEventsLogger {
     AppEventsLoggerImpl ส่วนตัว loggerImpl;

    สาธารณะ InternalAppEventsLogger ( บริบท บริบท ) {
        loggerImpl =  ใหม่ AppEventsLoggerImpl (บริบท, null , null );
    }

    ประชาชน InternalAppEventsLogger ( บริบท บริบท , String  applicationId ) {
        loggerImpl =  ใหม่ AppEventsLoggerImpl (บริบท, applicationId, null );
    }

    สาธารณะ InternalAppEventsLogger (
            สตริง กิจกรรมชื่อ
            String  applicationId ,
            การ เข้าถึง Token การเข้าถึง Token ) {
        loggerImpl =  ใหม่ AppEventsLoggerImpl (activityName, applicationId, accessToken);
    }

    ประชาชน เป็นโมฆะ LogEvent ( String  EventName , Bundle  พารามิเตอร์ ) {
        if ( FacebookSdk . getAutoLogAppEventsEnabled ()) {
loggerImpl            logEvent (eventName, พารามิเตอร์);
        }
    }

     โมฆะ สาธารณะlogEvent ( String  eventName , double  valueToSum , พารามิเตอร์Bundle  ) {
        if ( FacebookSdk . getAutoLogAppEventsEnabled ()) {
loggerImpl            logEvent (eventName, valueToSum, พารามิเตอร์);
        }
    }

     โมฆะ สาธารณะlogPurchaseImplicitly (
            BigDecimal  purchaseAmount , สกุล เงินสกุลเงิน , พารามิเตอร์Bundle  ) {
        if ( FacebookSdk . getAutoLogAppEventsEnabled ()) {
loggerImpl            logPurchaseImplicitly (
                    purchaseAmount,
                    สกุลเงิน
                    พารามิเตอร์
            );
        }
    }

     โมฆะ สาธารณะlogEventImplicitly ( String  eventName ,
                         การ ซื้อจำนวนมากครั้งใหญ่
                         สกุลเงิน สกุลเงิน ,
                          พารามิเตอร์บันเดิล ) {
        if ( FacebookSdk . getAutoLogAppEventsEnabled ()) {
loggerImpl            logEventImplicitly (
                    EventName,
                    purchaseAmount,
                    สกุลเงิน
                    พารามิเตอร์);
        }
    }

     โมฆะ สาธารณะlogEventImplicitly ( String  eventName ) {
        if ( FacebookSdk . getAutoLogAppEventsEnabled ()) {
loggerImpl            logEventImplicitly (eventName, null , null );
        }
    }

    ประชาชน เป็นโมฆะ logEventImplicitly ( String  EventName , ดับเบิล valueToSum , Bundle  พารามิเตอร์ ) {
        if ( FacebookSdk . getAutoLogAppEventsEnabled ()) {
loggerImpl            logEventImplicitly (eventName, valueToSum, พารามิเตอร์);
        }
    }

    ประชาชน เป็นโมฆะ logEventImplicitly ( String  EventName , Bundle  พารามิเตอร์ ) {
        if ( FacebookSdk . getAutoLogAppEventsEnabled ()) {
loggerImpl            logEventImplicitly (eventName, null , พารามิเตอร์);
        }
    }

    สาธารณะ คง FlushBehavior  getFlushBehavior () {
        กลับ AppEventsLoggerImpl getFlushBehavior ();
    }

     โมฆะ สาธารณะflush () {
loggerImpl        ล้าง ();
    }

     ผู้บริหาร แบบคงที่getAnalyticsExecutor () {
        กลับ AppEventsLoggerImpl getAnalyticsExecutor ();
    }

     String  คงที่getPushNotificationsRegistrationId () {
        กลับ AppEventsLoggerImpl getPushNotificationsRegistrationId ();
    }

     โมฆะสาธารณะคงที่ setUserData ( Bundle สุดท้ายuserData ) {   
        UserDataStore setUserDataAndHash (UserData);
    }

    @RestrictTo ( RestrictTo . Scope . GROUP_ID )
     โมฆะสาธารณะคงที่ setInternalUserData ( แผนที่สุดท้าย< String , String > ud ) {   
        UserDataStore setInternalUd (UD);
    }
}
