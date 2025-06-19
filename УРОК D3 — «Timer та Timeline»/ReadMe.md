## Урок «Timer та Timeline»

### Короткий опис
> Контролюємо час і плавно анімуємо будь-які параметри без зайвого Tick.  
> Після уроку ви зрозумієте, **коли** вибирати `SetTimer…`, а **коли** — `Timeline`.

| Блок | Що вивчаємо | Практика |
| :- | :- | :- |
| **Timer Basics** | `Set Timer by Function/Event`, `Clear/Invalidate` | Створюємо раз на 2 с повідомлення |
| **Advanced Timers** | `Pause/Unpause`, Handle Validity | Ставимо таймери на паузу або знищеємо їх |
| **Timeline Basics** | Update/Finished pins, Float & Vector tracks, Length & PlayRate | Робимо двері зі сповільненим відкриттям і еase-in |

---

### Q&A

| Питання | Відповідь |
| --- | --- |
| **Timer чи Timeline для інтерполяції?** | Timeline має вбудований криві (ease) + Update щокадрово → ідеальний для плавної анімації; Timer — дискретні виклики з фіксованим інтервалом. |
| **Чому Timer «проскакує» на слабких ПК?** | Timer спрацьовує після **min(DesiredTime, ΔTime)** — великі «фризи» збільшують крок. Для критично точного таймінгу використовуйте Timeline або Tick + Accumulator. |
| **Як зупинити всі таймери актора?** | `GetWorldTimerManager().ClearAllTimersForObject(this)` (C++) чи `Clear Timer by Handle` у циклі (BP). |

---

### Лайфхаки та рекомендації

- **One Timer — One Handle:** зберігайте `TimerHandle` у змінній → легше паузити / перезапускати.  
- **Timer у Component:** логіку cooldown’ів переносіть у Actor Component → багато акторів — один код.  
- **Ease без кривих:** у Timeline увімкніть **Auto Ease** для швидкого «quad-in/out».  
- **Preview в редакторі:** клікніть 👁️ поруч із треком → в Details побачите результат без запуску гри.  
- **PlayRate = -1:** дозволяє миттєво «реверснути» Timeline, не створюючи додаткового Reverse-виклику.  
- **Нульовий Timer як дебаунс:** `SetTimer(0.1 с, Looping = false)` замість Delay — відмінно «гасить» спам подій.  

> *Timer* — точка-у-точку, *Timeline* — безшовна анімація. Зберігайте Handle, реплікуйте стан, а не подію, і ніколи не залишайте нескінченних таймерів у фоні.
