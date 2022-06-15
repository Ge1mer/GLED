# GLED
## Addressable light strip controller

## Плата для управления адресными лентами и гирляндами прошивкой WLED

Есть такой проект [QuinLed](https://quinled.info/addressable-digital-leds/). Очень интересная задумка. Но одна из проблем, что это зарубежный проект и в нынешнее время купить и получить такой товар несколько сложно.
Решено было реализовать собственную плату, ну и попутно внести кое какие доработки.

Основой платы является контроллер ESP32. Как известно при подключении лент к пинам контроллера напрямую зачастую возникают проблемы, из за несоответствия уровней логики.
На плате установлен level shifter который обеспечивает необходимые уровни.
Для лент реализовано 4 канала управления.
Питание платы может быть любое от 5 до 24 вольт. Конфигурация задается с помощью джампера: 5 вольт, и больше 5 вольт. 
Прошивка WLED умеет управлять реле, для отключения силового питания на светодиоды, в плате выведен пин для подключения реле. Управляется низким уровнем. Можно подключать и чисто реле на 5 вольт, также различные модули с реле, управляемые низким уровнем.
На плате выведены контакты для подключения кнопки, с помощью которой можно переключать режимы лент.
Так же дополнительно выведены 4 GPIO для подключения датчиков движения концевиков и т. д. Есть возможность установки стандартного ИК приемника.
## Варианты подключения платы:
## Без управления силовым питанием. 
(https://github.com/Ge1mer/GLED/blob/main/%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D0%B0%D1%8F%20%D1%81%D1%85%D0%B5%D0%BC%D0%B0.jpg)
Блок питания подключаем к силовым контактам, устанавливаем перемычку в зависимости от напряжения питания. Ленты подключаем к выходным клеммам. 4 выходных канала подключены к индивидуальным предохранителям, еще два дополнительных вывода питания на одном предохранителе. Красный клеммник - плюс питания, зеленый клеммник - минус питания, синий клеммник сигнальный. Проверял работу с лентами WS2811, SK6812 и WS2801. Последняя лента требует два входа, данные и синхронизация. Конфигурация задается в веб интерфейсе.
## Управление силовым питанием.
Мощный блок питания подключаем к силовым контактам. Дополнительный блок питания подключаем к клеммнику Ext5V. Реле подключаем к клемме Rel и плюсу питания дополнительного блока. Перемычку на плате удалаяем. 220 вольт мощного блока питания подключаем через контакты реле. При выключении ленты из интерфейса, реле отключает мощный блок питания от сети. 
Дополнительный блок питания можно подключить к разъёму microUSB.

Плата содержит импульсный блок питания на 5 вольт, и при подключении по первому варианту на клеммнике Ext5V будет 5 вольт. можно подключать дополнительные потребители до 0.5 А.

Таблица выводов:

![image](https://user-images.githubusercontent.com/67655901/173756686-cc117d0c-c16f-4767-9f32-5af5b6070239.png)

Платы можно приобрести в [магазине] (https://espdomofon.ru/). Как обычно, платы прошитые, готовы к работе из коробки.
