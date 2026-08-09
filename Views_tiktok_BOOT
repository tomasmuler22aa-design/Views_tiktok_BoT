#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
█████████████████████████████████████████████████████████████
█  🚀 AHMAD ULTIMATE VIEWS BOT - الإصدار النهائي 🚀        █
█  ✅ زيادة مشاهدات تيك توك الفعلية                        █
█  ⚡ تحكم كامل بالخيوط والمشاهدات                         █
█  🖥️  يشتغل على اللابتوب                                  █
█████████████████████████████████████████████████████████████
"""

import os
import sys
import time
import random
import threading
import subprocess
from datetime import datetime

# ================== تثبيت المكتبات ==================
def install_packages():
    packages = ['selenium', 'webdriver-manager', 'colorama']
    for pkg in packages:
        try:
            __import__(pkg.replace('-', '_'))
        except ImportError:
            print(f"📦 جاري تثبيت {pkg}...")
            subprocess.check_call([sys.executable, "-m", "pip", "install", pkg])

install_packages()

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager
from colorama import init, Fore, Style

init(autoreset=True)

# ================== الألوان ==================
R = Fore.RED
G = Fore.GREEN
Y = Fore.YELLOW
C = Fore.CYAN
M = Fore.MAGENTA
W = Fore.WHITE
B = Fore.BLUE      # ✅ تمت الإضافة
S = Style.RESET_ALL

# ================== الشعار ==================
def banner():
    os.system('cls' if os.name == 'nt' else 'clear')
    print(f"""{C}
╔══════════════════════════════════════════════════════════════╗
║  {W} █████╗ ██╗  ██╗███╗░░░███╗ █████╗ ██████╗░{C}             ║
║  {W}██╔══██╗██║  ██║████╗░████║██╔══██╗██╔══██╗{C}             ║
║  {W}███████║███████║██╔████╔██║███████║██║░░██║{C}             ║
║  {W}██╔══██║██╔══██║██║╚██╔╝██║██╔══██║██║░░██║{C}             ║
║  {W}██║░░██║██║░░██║██║░╚═╝░██║██║░░██║██████╔╝{C}             ║
║  {W}╚═╝░░╚═╝╚═╝░░╚═╝╚═╝░░░░░╚═╝╚═╝░░╚═╝╚═════╝░{C}             ║
║                                                                  ║
║     {W}🚀 AHMAD ULTIMATE VIEWS BOT {R}PRO{C}                      ║
║     {Y}⚡ تحكم كامل - سرعة خارقة{C}                              ║
╚══════════════════════════════════════════════════════════════╝
{R}══════════════════════════════════════════════════════════════{S}
    """)

# ================== إنشاء متصفح متقدم ==================
def create_driver():
    """إنشاء متصفح Chrome مخفي"""
    options = Options()
    
    # إخفاء المتصفح
    options.add_argument('--headless=new')
    options.add_argument('--no-sandbox')
    options.add_argument('--disable-dev-shm-usage')
    options.add_argument('--disable-gpu')
    options.add_argument('--disable-blink-features=AutomationControlled')
    options.add_experimental_option("excludeSwitches", ["enable-automation"])
    options.add_experimental_option('useAutomationExtension', False)
    
    # إعدادات عشوائية
    options.add_argument(f'user-agent=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/{random.randint(118, 122)}.0.0.0 Safari/537.36')
    options.add_argument('--window-size=1280,720')
    
    # إعدادات لتوفير الموارد
    options.add_argument('--disable-images')
    options.add_argument('--blink-settings=imagesEnabled=false')
    
    try:
        service = Service(ChromeDriverManager().install())
        driver = webdriver.Chrome(service=service, options=options)
        
        # إخفاء هوية البوت
        driver.execute_cdp_cmd('Page.addScriptToEvaluateOnNewDocument', {
            'source': '''
                Object.defineProperty(navigator, 'webdriver', {
                    get: () => undefined
                });
            '''
        })
        return driver
    except Exception as e:
        print(f"{R}❌ خطأ في إنشاء المتصفح: {e}{S}")
        return None

# ================== مشاهدة فيديو ==================
def watch_video(driver, video_url, duration=4):
    """تشغيل الفيديو ومشاهدته بسرعة"""
    try:
        driver.get(video_url)
        time.sleep(1)
        
        # العثور على الفيديو وتشغيله
        video = driver.find_element(By.TAG_NAME, 'video')
        driver.execute_script("arguments[0].play();", video)
        
        # مشاهدة سريعة
        for i in range(duration):
            time.sleep(1)
            if random.random() > 0.9:
                driver.execute_script(f"window.scrollBy(0, {random.randint(-20, 50)});")
        
        return True
        
    except Exception as e:
        return False

# ================== البوت الرئيسي ==================
def start_views():
    """بدء رشق المشاهدات مع تحكم كامل"""
    banner()
    
    # رابط الفيديو
    video_url = input(f"{C}🔗 رابط الفيديو: {S}").strip()
    if not video_url:
        print(f"{R}❌ الرابط لا يمكن أن يكون فارغاً!{S}")
        return
    
    # عدد المشاهدات المطلوبة
    while True:
        try:
            total_views = int(input(f"{C}📊 عدد المشاهدات المطلوبة: {S}").strip())
            if total_views > 0:
                break
            print(f"{R}❌ أدخل عدد صحيح موجب!{S}")
        except ValueError:
            print(f"{R}❌ أدخل عدد صحيح!{S}")
    
    # عدد الخيوط المطلوبة
    while True:
        try:
            threads = int(input(f"{C}🧵 عدد الخيوط (1-50): {S}").strip())
            if 1 <= threads <= 50:
                break
            print(f"{R}❌ أدخل عدد بين 1 و 50!{S}")
        except ValueError:
            print(f"{R}❌ أدخل عدد صحيح!{S}")
    
    # مدة المشاهدة
    try:
        duration = int(input(f"{C}⏱️ مدة المشاهدة (ثواني): {S}").strip())
        duration = max(3, min(10, duration))
    except ValueError:
        duration = 4
    
    # حساب الوقت
    estimated_hours = (total_views * duration) / (threads * 3600)
    estimated_minutes = (total_views * duration) / (threads * 60)
    
    print(f"""
{Y}══════════════════════════════════════════════════════════════{S}
{G}🔥 بدء رشق {total_views:,} مشاهدة!{S}
{C}📊 العدد: {total_views:,} مشاهدة{S}
{C}🧵 الخيوط: {threads} متصفح متزامن{S}
{C}⏱️ المدة لكل مشاهدة: {duration} ثانية{S}
{C}⏰ الوقت المتوقع: ~{estimated_hours:.1f} ساعات ({estimated_minutes:.0f} دقيقة){S}
{C}📈 السرعة المتوقعة: ~{threads/duration:.1f} مشاهدة/ثانية{S}
{C}🖥️  الوضع: متصفح مخفي (Headless){S}
{Y}══════════════════════════════════════════════════════════════{S}
    """)
    
    # تحذير حسب عدد الخيوط
    if threads > 20:
        print(f"{Y}⚠️ تنبيه: {threads} خيط ستستهلك ~{threads * 0.4:.1f}-{threads * 0.6:.1f} GB رامات!{S}")
        print(f"{Y}⚠️ تأكد من تبريد الجهاز بشكل جيد{S}")
    
    confirm = input(f"{Y}⚠️ هل تريد المتابعة؟ (y/n): {S}").strip().lower()
    if confirm != 'y':
        print(f"{Y}⏹️ تم الإلغاء{S}")
        return
    
    print(f"\n{G}🚀 جاري التشغيل...{S}\n")
    
    success = 0
    failed = 0
    start_time = time.time()
    running = True
    active_threads = 0
    lock = threading.Lock()
    
    def worker():
        nonlocal success, failed, running, active_threads
        with lock:
            active_threads += 1
        
        while running and success < total_views:
            driver = None
            try:
                driver = create_driver()
                if driver and watch_video(driver, video_url, duration):
                    with lock:
                        success += 1
                        if success % 100 == 0:
                            print(f"{G}✅ مشاهدة #{success:,}/{total_views:,}{S}")
                else:
                    with lock:
                        failed += 1
                        if failed % 100 == 0:
                            print(f"{R}❌ فشل #{failed:,}{S}")
            except Exception as e:
                with lock:
                    failed += 1
            finally:
                try:
                    if driver:
                        driver.quit()
                except:
                    pass
                time.sleep(random.uniform(0.1, 0.3))
        
        with lock:
            active_threads -= 1
    
    # تشغيل الخيوط
    thread_list = []
    for i in range(threads):
        t = threading.Thread(target=worker, name=f"Worker-{i+1}")
        t.daemon = True
        t.start()
        thread_list.append(t)
        time.sleep(0.05)
    
    # مراقبة التقدم
    try:
        last_success = 0
        stall_count = 0
        
        while success < total_views and running:
            time.sleep(5)
            elapsed = int(time.time() - start_time)
            rate = success / elapsed if elapsed > 0 else 0
            progress = (success / total_views) * 100
            
            sys.stdout.write(f"\r{C}⏳ التقدم: {success:,}/{total_views:,} ({progress:.1f}%) | "
                           f"❌ فشل: {failed:,} | "
                           f"⏱️ {elapsed//3600}س {elapsed//60%60}د | "
                           f"📊 {rate:.2f}مش/ث | "
                           f"🧵 {active_threads} خيط{S}")
            sys.stdout.flush()
            
            # إعادة تشغيل الخيوط المتوقفة
            if success == last_success and elapsed > 30:
                stall_count += 1
                if stall_count >= 3:
                    print(f"\n{Y}⚠️ إعادة تشغيل الخيوط...{S}")
                    for _ in range(3):
                        new_t = threading.Thread(target=worker)
                        new_t.daemon = True
                        new_t.start()
                        thread_list.append(new_t)
                        time.sleep(0.1)
                    stall_count = 0
            else:
                stall_count = 0
            
            last_success = success
    
    except KeyboardInterrupt:
        running = False
        print(f"\n\n{Y}⏹️ تم الإيقاف يدوياً{S}")
    
    # النتائج
    elapsed = int(time.time() - start_time)
    print(f"""
{G}══════════════════════════════════════════════════════════════{S}
{G}✅ اكتمل الرشق!{S}
{G}✅ المشاهدات الناجحة: {success:,}{S}
{R}❌ المشاهدات الفاشلة: {failed:,}{S}
{C}⏱️ الوقت المستغرق: {elapsed//3600} ساعات و {elapsed//60%60} دقيقة{S}
        """)
    
    if elapsed > 0:
        print(f"{Y}📊 معدل النجاح: {success/elapsed:.2f} مشاهدة/ثانية{S}")
        print(f"{Y}📊 متوسط السرعة: {(success/elapsed)*3600:.0f} مشاهدة/ساعة{S}")
        total_attempts = success + failed
        if total_attempts > 0:
            print(f"{M}📈 نسبة النجاح: {(success/total_attempts*100):.1f}%{S}")
    
    print(f"{G}══════════════════════════════════════════════════════════════{S}")
    
    input(f"\n{Y}اضغط Enter للمتابعة{S}")

# ================== القائمة ==================
def main():
    while True:
        banner()
        print(f"""
{B}┌─────────────────────────────────────────────────────────────┐
│  {W}1 {B}🚀 رشق مشاهدات (تحكم كامل)                         │
│  {W}2 {B}🚪 الخروج                                         │
└─────────────────────────────────────────────────────────────┘
        """)
        
        choice = input(f"{C}❓ اختر: {S}").strip()
        
        if choice == '1':
            start_views()
        elif choice == '2':
            print(f"\n{G}👋 وداعاً!{S}")
            sys.exit(0)
        else:
            print(f"{R}❌ خيار غير صحيح!{S}")
            time.sleep(1)

if __name__ == "__main__":
    try:
        main()
    except KeyboardInterrupt:
        print(f"\n{Y}⏹️ تم الإلغاء{S}")
        sys.exit(0)
    except Exception as e:
        print(f"{R}❌ خطأ غير متوقع: {e}{S}")
        sys.exit(1)
