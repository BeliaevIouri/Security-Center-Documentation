## Менеджер объектов

Модуль «Менеджер объектов» предназначен для управления описанием имеющихся в программном обеспечении «Центр охраны» объектах.

### Объект

На вкладке «Объект» можно указать основную описательную информацию об объекте: номер, название, адрес, телефоны и так далее.

### Разделы

Вкладка «Разделы» позволяет сохранить информацию о том, на какие разделы (области) разбит объект и какое оборудование используется для организации разделов на объекте. 

Список оборудования, установленного в разделе, можно изменить в модуле «Настройка системы» — на вкладке «Поля объектов», поле «*Оборудование раздела объекта».

Необходимо отметить, что механизм описания разделов на объекте позволяет решать следующие задачи:

* _Разделы, идентифицируемые порядковыми номерами_. Эта актуально для панелей, которые поддерживают функцию объединения шлейфов в независимые разделы, и для которых протокол «Contact ID» является «родным».
* _Области, идентифицируемые объектовыми номерами_. Эта возможность нужна для панелей, которые не используют протокол «Contact ID» для передачи информации в центр мониторинга, но поддерживают объединение шлейфов в независимые области, каждая из которых имеет свой собственный номер объекта.
* Объекты, использующие разные номера при работе по разным каналам связи. 
Такая ситуация возможна в том случае, если на уже оборудованные объекты устанавливаются дополнительные коммуникаторы (например, радиопередатчики), но номера объектов, на которые они устанавливаются, уже используются в радиоканале. В этом случае можно запрограммировать панель так, чтобы по телефону и по радио использовались разные номера объектов, описав эти номера в качестве разделов объекта.

### Шлейфы 

На вкладке «Шлейфы» можно детально описать используемые рубежи охраны объекта, включая информацию об используемом оборудовании и принадлежности шлейфов разделам объекта.
Список оборудования, установленного в шлейфе, можно изменить в модуле «Настройка системы» — на вкладке «Поля объектов», поле «*Оборудование шлейфа объекта».

Информация о шлейфах является очень важной частью описания объекта, так как она используется при генерации описании событий, полученных с объекта. Так, если с объекта будет получено извещение о тревоге в шлейфе номер один, то в описание события, которое будет создано для обработки оператором «Центра охраны», будет подставлено описание шлейфа номер один из карточки объекта. 

### Ответственные лица

Вкладка «Ответственные лица» предназначена для ввода информации об ответственных за объект лицах: имена, адреса, номера телефонов. Рекомендуется включать в ответственные лица пользователей владеющих персональным кодом постановки/снятия объекта с охраны, причем номер кода пользователя, запрограммированный в панели должен соответствовать номеру ответственного лица. В этом случае так же, как и со шлейфами — информация о пользователе, выполнившем постановку или снятие, будет включена в описание события, обрабатываемого оператором «Центра охраны».

### Охрана

На вкладке «Охрана» можно изменить параметры, связанные с правилами и режимом охраны объекта.

_Поставить на длительную охрану_. Поле предназначено для включения режима длительной охраны объекта и указания времени действия данного режима. Режим длительной охраны предназначен для контроля ситуаций, когда объект по каким-то причинам длительное время будет (или должен) находиться под охраной. 

Контроль длительной охраны объекта осуществляется следующим образом: 

* при наступлении времени начала длительной охраны производится проверка факта постановки объекта под охрану. 
* если объект не под охраной, создается системное событие с кодом `ZZXC`. В случае, если объект продолжает оставаться не под охраной, системное событие с кодом `ZZXC` будет повторяться с интервалом, указанным в настройках Менеджера событий. 
* если в интервал, указанный в качестве времени длительной охраны объект будет снят с охраны, будет создано системное событие с кодом `ZZXE`, после чего, соответственно, цикл контроля длительной охраны начнется заново — с генерацией системного события с кодом `ZZXC` и ожиданием постановки объекта на охрану.

_Отключить объект_. Поле предназначено для отключения объекта, начиная с какого-то времени. Если объект отключен, полученные с него события обрабатываются следующим образом:

* Во-первых, при приеме всех этих событий Дежурным оператором отключается звуковое сопровождение. То есть, все события продолжают отображаться, события с типами классов Постановка на охрану и Снятие с охраны продолжают изменять статус объекта, только отсутствует звук при приеме событий с этого объекта.

* Во-вторых, при приеме событий с типом класса Тревога, система (если конкретно — Менеджер событий) создает отмену для них. Другими словами, если объект отключен и с него приходит тревога, то в дополнении к тому, что звук тревоги отсутствует, эта тревога еще и автоматически отменяется.

_Автоматически включить объект_. В случае, если объект отключен, данное свойство позволяет автоматически включить его при наступлении указанного времени.

### Контрольное время

Вкладка «Контрольное время» предназначена для управления одним из важнейших параметров контроля работы объекта.

Контрольным временем объекта называется временной интервал, в течении которого с объекта должно быть получено любое событие. Любое событие означает, что событие может быть получено по любому из каналов связи (например, радио, телефон), а может быть системным. В случае, если событие за интервал не получено, создаётся системное событие с кодом `ZZXA`. 

Настройку контрольного времени объекта можно выполнить так, чтобы отдельно контролировать все каналы связи, используемые объектом. 

### Расписание охраны

На вкладке «Расписание охраны» можно указать для каждого дня недели периоды времени, когда объект должен находиться под охраной, а также включить контроль этого правила «Центром охраны».

### Шаблон событий

Вкладка «Шаблон событий» предназначена для изменения шаблона кодов событий, который используется при описании принятых с объекта событий, отключения тревожных событий, а также для изменения свойств конкретного кода события для данного объекта. 

Необходимо отметить, что качество шаблонов событий, поставляемых с новыми версиями «Центра охраны» постоянно улучшается, поэтому при описании объектов рекомендуется использовать самые последние версии шаблонов событий.

Для того, чтобы заменить устаревший шаблон событий на его новейшую версию, можно воспользоваться функцией замены шаблона событий, реализованной в модуле «Настройка системы».

На вкладке «Шаблон событий» можно изменить описание любого события. При этом необходимо понимать, что сделанные изменения коснутся только данного объекта и не будут отражены ни в базовом шаблоне кодов событий, ни в каком-либо другом объекте. Вследствие того, что изменения шаблона событий для объекта исключительно сложно контролировать, рекомендуется не прибегать к ним без критической необходимости.

Отключение тревожного события по своему значению очень похоже на отключение объекта, с тем лишь отличием, что речь идет только об одном коде события. При приеме отключенного события в модуле «Дежурный оператор» отсутствует звуковое сопровождение события, а «Менеджером событий» создается автоматическая отмена для данной тревоги. Необходимо подчеркнуть, что в отличие от отмены тревоги для отключенного объекта, отмена тревоги для отключенного события отменит только это событие — охрана объекта продолжается в полном объеме, за исключением отключенного кода события.

Отключение события возможно только на ограниченный временной интервал, который указывается при выполнении отключения. По истечении этого интервала — событие будет автоматически включено. Отключенное событие можно в любой момент включить вручную.

Все операции по отключению и включению события сопровождаются созданием системных событий. Так, при отключении события создается системное событие с кодом `ZZXM`, при автоматическом включении события создается системное событие с кодом `ZZXN`, а при включении события оператором (ручном включении) создается системное событие с кодом `ZZXO`. 

Генерация системных событий позволяет четко отслеживать операции по отключению событий.

### Дополнительные характеристики

На вкладке «Дополнительные характеристики» можно указать значения дополнительных характеристик объектов (пользовательских полей). Управление списком полей осуществляется в модуле «Настройка системы».

Если значение какой-то дополнительной характеристики для объекта не определено, ее значение можно оставить пустым. При отображении дополнительных характеристик в карточке объекта в списке характеристик присутствуют только те, значение для которых указано.

### Альтоника

Вкладка «Альтоника» предназначена для того, чтобы настроить параметры объекта, специфичные для оборудования производства компании «Альтоника».

#### Тип оборудования

Для корректной работы алгоритмов обработки сигналов «Центра охраны» необходимо указать правильный тип системы используемого на объекте оборудования: «Lonta-202» или «RS-200». В случае, если на объекте установлено оборудование другой системы, нужно указать тип «Другой».

#### Уровни сигнала

Для объекта, на котором используется оборудование системы «Lonta-202» можно изменить значение для пороговых уровней сигнала, принимаемого с объекта. Если уровень сигнала, принимаемого с объекта, станет меньше значения, заданного в поле «Уровень предупреждения», то будет создано системное событие с кодом `ZZXV`. Если же уровень сигнала, принимаемого с объекта, будет меньше значения, заданного в поле «Уровень тревоги», то будет создано системное событие с кодом `ZZXU`. С помощью системных событий с кодами `ZZXV` и `ZZXU` можно автоматически контролировать уровень сигнала, принимаемого с объектов, привлекая внимание оператора только к тем объектам, где требуется его вмешательство.

Необходимо отметить, что для объектов, на которых установлено оборудование системы «Lonta-202» в модуле «Дежурный оператор» доступна функция просмотра принимаемого уровня сигнала. В карточке объекта присутствует закладка, которая позволяет отобразить уровень сигнала в виде графика или в виде таблицы значений.

#### Передатчик

В ситуации, когда несколько объектовых приборов подключаются к одному радиопередатчику системы «Lonta-202», для идентификации таких приборов необходимо указать объектовый номер передатчика в поле «Номер объекта», а номер раздела, который соответствует прибору, в поле «Номер раздела». 

Значения, указанные в полях «Номер объекта» и «Номер раздела» являются приоритетными по отношению к стандартным номерам объектов «Центра охраны»: при приеме событий сначала просматриваются значения, введенные на закладке «Альтоника» и только потом — значения номеров объектов.

