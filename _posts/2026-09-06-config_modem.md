---
title: "کانفیگ مودم فیبر نوری برای اتصال به اینترنت و تلفن بصورت همزمان"
categories:
  - Trick
tags:
  - wifi
  - مودم
  - فیبر_نوری
  - اینترنت
  - مخابرات
---

در صورتی که برای ساختمان شما فیبر نوری کشیده شده است و می‌خواهید خط تلفن و اینترنت داشته باشید توسط این مطلب روش کانفیگ را یاد خواهید گرفت.

---

تفاوتی که در این نوع مودم‌های فیبر نوری با adsl قدیم وجود دارد این است که بصورت همزمان هم برای اتصال به اینترنت و هم برای استفاده از تلفن باید از یک مودم استفاده کنید و دیگر ورودی‌های تلفن قدیمی ساختمان کار نمی‌کنند.  

### وارد شدن به بخش تنظیمات مودم
در پشت مودم یک بخش برای اتصال سیم تلفن به آن و یکی هم برای اتصال خط فیبر آمده به ساختمان وجود دارد.  
بعد از اتصال برای کانفیگ مودم نیاز است به آدرسی که در پشت مودم نوشته شده است وارد شوید، اگر می‌خواهید با موبایل کانفیگ را انجام دهید ابتدا نیاز است توسط Wifi به شبکه‌ای که اطلاعات آن در پشت مودم آمده وصل شوید و در غیر این صورت با سیم Lan لپ تاپ خود را به مودم وصل کنید.  
بطور مثال در عکس زیر آدرس `192.168.100.1` است.  
دقت کنید با اطلاعات ورودی که در پشت مودم وجود دارد به تمام تنظیمات دسترسی ندارید، بطور مثال اگر با `root/admin` وارد شوید نمی‌توانید بخش اتصال به اینترنت و تلفن را کانفیگ کنید. برای رفع این مشکل اگر مودم شما از برند Huawei هست از نام‌کاربری `telecomadmin` و رمز عبور `admintelecom` باید استفاده کنید.  

### تنظیمات اتصال به اینترنت
برای اتصال به اینترنت نیاز است یک `WAN` جدید ایجاد کنید. برای این کار به سربرگ WAN بروید و روی `New Connection` کلیک کنید.  
در این بخش نیاز است تنظیمات مشابه عکس زیر را وارد کنید. مهم‌ترین آیتم این بخش مقدار `VLAN ID` است که با توجه به شهر ممکن است تفاوت داشته باشد. اگر با مقدار زیر اتصال برقرار نشد نیاز است مقدار آن را از پشتیبانی در سایت زیر بگیرید.  
همچنین مقدار `Username` و `Password` نیز در سایت زیر دردسترس است.  

[myftth](https://myftth.tci.ir)  


 - Enable WAN : Tick
 - Connection Mode : PPPoE
 - Protocol Type : IPv4
 - WAN Mode : Route WAN
 - Service Type : INTERNET
 - Enable VLAN : Tick
 - VLAN ID : 80
 - 802.1p Policy : Use the specified value
 - 802.1p : 0
 - MRU : 1492
 - User Name : From myftth
 - Password : From myftth
 - Enable LCP Detection : Un Check
 - Binding Options : SSID1
 - *---*
 - Ip Acquisition Mode : PPPoE
 - Enable NAT : Tick
 - NAT Type : Port-restricted cone NAT
 - Dialing Method : Automatic
 - Multicast VLAN ID : empty

سپس بر روی `Apply` کلیک کنید.  
اکنون اگر به سربرگ `Status` بروید در بخش `WLAN Information`  باید مودم با موفقیت به اینترنت متصل شده باشد.  


### تنظیمات اتصال تلفن
برای اتصال به تلفن علاوه بر WAN نیاز به تنظیم Voice هم وجود دارد. برای این کار ابتدا به سربرگ `WAN` بروید و بر روی `New Connection` کلیک کنید.  
اکنون کافی است اطلاعات را مشابه زیر پر کنید. دقت کنید که مقادیر IP ممکن است با توجه به استان متفاوت باشد.  
همچنین مقدار VLAN ID نیز ممکن است با توجه به استان متفاوت باشد. در صورت کار نکردن نیاز است مقادیر را از پشتیبانی که لینک آن در بالا آمده دریافت کنید یا از لینک زیر گزارش خرابی ثبت کنید:  

[tci](https://my.tci.ir/dashboard/home)

 - Enable WAN : Tick
 - Connection Mode : IPoE
 - Protocol Type : IPv4
 - WAN Mode : Route WAN
 - Service Type : VIOP
 - Enable VLAN : Tick
 - VLAN ID : 71
 - 802.1p Policy : Use the specified value
 - 802.1p : 5
 - MRU : 1500 
 - *---*
 - Ip Acquisition Mode : Static
 - Enable NAT : Tick
 - Ip Address : 10.96.64.73
 - Default Gateway : 10.96.64.73
 - Subnet Mask : 255.255.255.0
 - Primary DNS Server : empty
 - Secondary DNS Server : empty

سپس بر روی `Apply` کلیک کنید.  
اکنون به سربرگ `Voice` بروید و اطلاعات آن را مشابه زیر پر کنید.  
در این بخش نیز مقدار Password و IP و Domain با توجه به استان ممکن است متفاوت باشد.  

- Outbound Proxy Server Address : empty
- Outbound Proxy Server Port : 5060
- Address of the Standby Outbound Proxy Server : empty
- Port of the Standby Outbound Proxy Server : 5060
- Address of the Primary Proxy Server : 10.217.65.70
- Port of the Primary Proxy Server : 5060
- Address of the Standby Proxy Server : empty
- Port of the Standby Proxy Server : 5060
- Home Domain: mn.tci1.ch1.ir
- Local Port : 5060
- Digitmap : don't change
- Digitmap Matching Mode : Min
- Registration Period : 600
- Signaling Port: 2_VOIP_R_VID_71 (مقدار WAN که ساختید)
- Media Port: 2_VOIP_R_VID_71 (مقدار WAN که ساختید)
- Region: Iran
-  *---*
- Enable User : Tick
- URI : +982100000000
- Registration User Name : +982100000000
- Associated POTS Port : 1
- Authentication User Name : 982100000000
- Password: *

سپس بر روی `Apply` کلیک کنید.  
اکنون اگر به سربرگ `Status` بروید در بخش `VoIP Information`  باید مودم با موفقیت به اینترنت متصل شده باشد.  