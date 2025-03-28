# Заказ pcb на `rezonit.ru`

## Общие рекомендации

* Заказ плат - кропотливая работа, ошибка на этом этапе может стоить достаточно дорого. Все ошибки придется исправлять собственными мощностями. 
* Новые устройства должны проходить проверку на тестовой партии малого объема.
* При повторном заказе той же ревизии платы не обязательно заново загружать `gerber` файлы. Можно сразу начать с [заказа pcb](#заказ-pcb "Да, да, жми сюда").

## Загрузка фотошаблонов

> [!TIP]
> Перед загрузкой gerber файлов проверь, возможно плата этой версии уже была загружена в личный кабинет.
> Нужно проверить правильно ли выбраны параметры у существующей платы.
> Если это так, то монжо сделать [повторный заказ](#повторный_заказ_pcb "повторный заказ pcb")

Все начинается с загрузки `gerber` файлов. Готовый архив нужно скачать в репозитории в `Releases`.

> [!NOTE]
> <details>
> <summary>Расшифровка названия проекта</summary>
> Файл проекта должен называться по шаблону *_v??.zip
> Где `*` - трех буквенный шифр проекта
> `v??` - версия (ревизия) проекта, без разделяющей точки.  Например, `rev 0.2` будет выглядеть как `v02`
>Файл используемый для заказа должен хранится в репозитории.
> </details>

> [!WARNING]
>  
> Если в архиве есть файлы *_v??-drl_map.gbr и/или *_v??-job.gbrjob , то их нужно удалить.
> Резонит не будет работать с таким архивом корректно.
>
> <details>
> <summary>Пример</summary>
>
>   ![Тут должна быть картинка, но она не загрузилась](https://github.com/Artel-Inc/faq/assets/48344616/fdd0efcd-bd59-46b4-bbbe-ab088d853cc2)
> 
> </details>

Нужно открыть раздел `список плат` > `новая плата`

![image-20240629124659041](design//image-20240629124659041.png)

Загрузите архив тут

![image-20240629124758036](design//image-20240629124758036.png)

На следующем этапе нужно включить все слои, выбрать тип слоя и расположить слои так, как они будут распологаться в плате.

> [!NOTE]
> <details>
> <summary>Расшифровка названии файлов слоев</summary>
> Тип слоя, который нужно выбрать указан после ревизии платы в формате *_v??-A_BBB.gbr, кроме слоя NCData и Border. 
> NCData слой имеет формат *_v??.drl, Border - *_v??-Edge_Cuts.gbr.
> 
> Где:
> 
> `*` - трех буквенный шифр проекта
> 
> `v??` - версия (ревизия) проекта
> 
> `A` - сторона, F - Top, B - Bottom
> 
> `BBB` - тип слоя. Слой Cu обозначается резонитом без типа слоя, как просто Top или Bottom
> 
> Нужно выбрать правильный тип слоя, например:
> 
> foo_v42-F_Paste.gbr - PasteTop
> 
> bar_v23-Edge_Cuts.gbr - Border
> 
> baz_v69-B_Cu - Bottom
> </details>

Сравните то, что у вас получилось с примером и жмите далее. Количество слоев может отличаться в зависимости от платы.

![image-20240629124817462](design//image-20240629124817462.png)

## Заказ PCB

Все настройки можно взять из `artel-inc/НАЗВАНИЕ_ПРОЕКТА/hardware/jlcpcb/`.
Там лежат настройки для JLCPCB, можно взять все настройки оттуда, кроме некоторых.
В резоните нужно доплачивать и дольше ждать за любую маску, кроме зеленой с белой шелкографией, по этому выбираем зеленую маску и белую шелкографию.
Панелизацию и разделение нужно согласовать с производством, которое делает монтаж. Размеры платы нормально определяются автоматически.
Срок выбрать в зависимости от текущей ситуации. Количество лучше указывать здесь же.

Должно получиться примерно так:

![image-20240629124830884](design//image-20240629124830884.png)

![image-20240629124843410](design//image-20240629124843410.png)

Далее выбираем срок и жмем `Добавить плату к заказу`

К заказу можно добавить несколько видов плат с разными сроками.
Производство трафаретов и монтажа заказывается отдельным заказом от заказа плат.

## Повторный заказ PCB

<details>
<summary>Повторный заказ PCB</summary>

Если плата уже была загружена в резонит заранее, то можно выбрать ее в меню плат и добавить к существующему заказу

![image-20240629125014496](design//image-20240629125014496.png)

![image-20240629125033714](design//image-20240629125033714.png)

Вводим необходимое количество плат и переходим к другому этапу

![image-20240629125054041](design//image-20240629125054041.png)

</details>

## Проверка/подтверждение заказа

Лучше что бы проверку заказа делал другой человек или же на следующий день после формирования заказа. 

Необходимо проверить:

- Перечень плат
- Количество плат
- Визуальный осмотр плат в предпросмотре (могут быть некоторые проблемы с предварительным просмотром, при возникновении нужно уточнить у менеджера дефект это предпросмотра или обработки платы)
- Версии/ревизии плат

Выберите контактное лицо, плательщика и доставку/самовывоз. Как показывает практика, самовывоз из офиса в г. Екатеринбург удобнее всего.

![image-20240629125104065](design//image-20240629125104065.png)

![image-20240629125115654](design//image-20240629125115654.png)

Через 1-2 рабочих дня черновик проверят и можно будет запускать платы в производство с предварительной оплатой.

> [!IMPORTANT]  
> Важно: Платы запустят в производство только после получения оплаты.

