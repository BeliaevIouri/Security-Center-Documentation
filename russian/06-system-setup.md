## Настройка системы

Модуль «Настройка системы» предназначен для изменения служебных справочников «Центра охраны», например, шаблонов событий или типов объектов.

### Классы событий

В программном обеспечении «Центр охраны» создаваемые события делятся на несколько типов:

* Тревога
* Предупреждение
* Постановка на охрану
* Снятие с охраны
* Неисправность
* Восстановление
* Исключение
* Тест
* Другое 
* Сброс

Тип события определяет способ его обработки. Так, события имеющие тип «Тревога» требуют обязательных действий оператора, называемых отработкой тревоги. Кроме того, тревоги, отработка которых не начата или не завершена, изменяют текущий статус объектов. При обработке событий, имеющих тип «Постановка на охрану» или «Снятие с охраны», статус объекта также меняется.

Список типов событий предопределен и не может быть изменен пользователем. Для того чтобы объединять события в группы и управлять ими — предназначены классы событий. Класс события определяет его тип, при этом можно создать несколько классов с типом «Тревога» и определить для каждого класса индивидуальные списки действий по тревоге и их отмен.

На вкладке «Классы событий» можно отредактировать список используемых классов событий. 

Класс события определяет внешний вид события в списке принятых событий модуля «Дежурный оператор». Цвет, гарнитуру шрифта, цвет фона, — все эти свойства класса событий можно изменить в модуле «Настройка системы».

Кроме атрибутов, отвечающих за отображение событий, есть возможность указать звуковой файл, который будет воспроизводиться при получении события.

Для классов событий, имеющих тип «Тревога», доступны для изменения списки действий и отмен, которые оператор может зарегистрировать, выполняя отработку тревоги. Важно, что можно определить не только список действия, но также и их последовательность. 

Если «Центр охраны» эксплуатируется достаточно давно, то есть вероятность, что список классов событий замусорен. Например, в нем встречаются классы-дубликаты, либо он содержит информацию о классах, которые уже не используются. Тем не менее, «Центр охраны» препятствует их удалению, потому что есть события, при описании которых эти классы используются. Для того, чтобы справиться с этой проблемой, есть возможность заменить дубликаты или не используемые классы событий на их актуальные аналоги.

### Шаблоны событий

Одно и то же событие, возникшее на объекте, может быть передано в «Центр охраны» по-разному. Формат извещения, в котором будет получена информация о событии, зависит от типа передающего оборудования и канала связи. 

Шаблоном событий называется список событий, которые могут быть получены при расшифровке извещений от объекта.

Шаблон событий является неотъемлемой характеристикой объекта. Указать шаблон событий, который должен использовать для объекта, можно в модуле «Менеджер объектов».

На вкладке «Шаблоны событий» можно изменить список шаблонов, используемых «Центром охраны». Кроме того, можно изменить описание событий, содержащихся в шаблоне.

При описании событий рекомендуется использовать макросы `%user%` и `%zone%`. Если при расшифровке события в его описании будет найден макрос, то в описание будет подставлено значение, соответствующее названию шлейфа (макрос `%zone%`) или имени ответственного (макрос `%user%`). При этом номер шлейфа или пользователя будет взят из самого события. 
Информация о шлейфах и ответственных лицах на объекте является очень важной. Внести эту информацию для объекта можно в модуле «Менеджер объектов».

Интересной особенностью описания события в шаблоне является возможность определить событие с точностью до канала связи, по которому оно принято. Таким образом, один и тот же код события, принятый, например, по телефону и GPRS, может быть описан по-разному.

Необходимо отметить, что качество шаблонов событий, поставляемых с новыми версиями «Центра охраны» постоянно улучшается, поэтому при описании объектов рекомендуется использовать самые последние версии шаблонов событий.
Для того, чтобы вместо устаревшего шаблона для объектов указать другой, более актуальный — можно воспользоваться функцией замены шаблона событий. 

### Действия

Вкладка «Действия» предназначена для изменения списка действий, которые оператор может зарегистрировать при отработке тревоги.

В программном обеспечении «Центр охраны» определены следующие типы действий:

* _Вызов группы_. При регистрации действия этого типа оператору необходимо будет указать группу реагирования, которая была вызвана на объект. Если на объект была вызвана группа, то тревогу по объекту можно отменить только после того, как будет зарегистрировано прибытие группы на объект или отмена ее вызова.

* _Прибытие группы_. Действие типа «Прибытие группы» доступно для регистрации только после того, как будет зарегистрирован вызов группы на объект. При регистрации действия с типом «Прибытие группы» оператор должен будет выбрать группу, прибытие которой он фиксирует.

* _Отмена вызова группы_. Регистрация отмены вызова группы доступна только после того, как будет зарегистрирован ее вызов на объект. При регистрации отмены вызова оператор должен будет выбрать группу, отмену вызова которой он выполняет.

* _Комментарий оператора_. Действие этого типа позволяет ввести оператору произвольный текст, связанный с процессом отработки тревоги. Действия этого типа могут быть зарегистрированы на любом этапе отработки тревоги. Рекомендуется включать действие этого типа в списки действий для всех тревог, имеющихся в «Центре охраны».

* _Другое_. Действия типа «Другое» носят информационный характер и используются для быстрой регистрации действий, часто используемых при отработке тревоги (звонок ответственному, вызов милиции и т.д.). Действия этого типа могут быть зарегистрированы на любом этапе отработки тревоги.
Список действия с типом «Другое» рекомендуется постоянно актуализировать, чтобы они соответствовали тактике охраны, используемой в настоящий момент. Хорошим источником для новых действий с типом «Другое» могут быть регистрируемые комментарии операторов.

Список групп реагирования, используемых «Центром охраны», можно изменить в модуле «Менеджер персонала».

### Отмены тревог

На вкладке «Отмены тревог» можно отредактировать список причин, регистрируемых при отмене тревоги.
Список доступных отмен тревог тесно связан с используемой тактикой охраны объектов и имеет большое значение при анализе эффективности работы предприятия.

Программное обеспечение «Центр охраны» содержит несколько аналитических отчетов, позволяющих оценить наиболее распространенные причины отмен тревог, в том числе и в разрезе объектов. 
Для того, чтобы этими отчетами можно было пользоваться, нужно поддерживать список отмен тревог в актуальном состоянии и четко регламентировать использование каждой отмены в инструкциях оператору.

### Типы объектов

Вкладка «Типы объектов» предназначена для управления списком типов объектов. Тип объекта является обязательным свойством объекта. Тип объекта используется для удобства организации (сортировки, группировки) списка объектов, например, при просмотре свойств объектов или создании отчетов. Указать тип для объекта можно в модуле «Менеджер объектов».

### Поля объектов

На вкладке «Поля объектов» можно изменить список дополнительных полей, которые будут доступны при заполнении карточки объекта.

При формировании списка полей можно задать порядок их следования при отображении в карточке объекта.

Если значения какого-то поля представляют собой список заранее известных значений, то можно заполнить этот список, указав для поля соответствующий тип. При этом, список значений не ограничивает возможность указать значение для поля объекта вручную, если это необходимо.
В списке полей объектов присутствуют два поля, для которых рекомендуется изменять только список возможных значений. Это поля «Оборудование раздела объекта» и «Оборудование шлейфа объекта». Как следует из их названий — они предназначены для того, чтобы при редактировании разделов и шлейфов объектов в модуле «Менеджер объектов» было удобнее заполнять значения для поля «Оборудование».

