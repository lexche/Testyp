## Урок 6. Файловые системы.

Представим: данные лежат на диске в “сыром” виде. Каждой программе-процессу придётся самостоятельно придумывать логику работы с этим сырьём. А как при этом разделять доступ к файлам разных пользователей? А обеспечить совместимость программ? А надёжность хранения?

Файловая система - это организация файлов и данных на устройствах хранения, таких как жесткие диски, флэш-накопители, карты памяти и другие носители информации. Она отвечает за размещение и управление файлами, организацию доступа к ним и обеспечивает безопасное хранение информации. Представь, что файловая система - это своего рода "каталог" для твоих файлов, где каждый файл имеет свое место и структуру.

Теперь, почему она нужна? А вот почему: без файловых систем мы просто не смогли бы эффективно хранить и находить данные, а также не смогли бы управлять файлами на наших устройствах.

Когда ты сохраняешь файл на компьютере или мобильном устройстве, файловая система помогает разместить его на диске, а затем позволяет нам находить, открывать и изменять этот файл. Без файловой системы все данные были бы как беспорядочная куча информации, и найти нужную информацию было бы как поиск иголки в стоге сена. Файловая система дает структуру этой информации и делает ее доступной для нас.

Так что файловая система - это наша главная система организации данных на компьютерах и других устройствах, и без нее работа с данными была бы какой-то беспорядок.

Есть большое количество файловых систем, рассмотрим основные из них:

- FAT (File Allocation Table)
  Ключевые характеристики:
  - Простая структура с использованием таблицы файловой выделения (FAT), для отслеживания расположения файлов на диске.
  - Поддерживается многими операционными системами.
  - Используется на съемных носителях, таких как флэш-накопители, SD-карты и др.
  - Однако, ограничена в поддержке файлов размером более 4 ГБ и не так эффективна как более современные файловые системы.

- NTFS (New Technology File System)
  Ключевые характеристики:
  - Разработана корпорацией Microsoft и является стандартной файловой системой для операционных систем семейства Windows.
  - Поддерживает метаданные, журналирование, расширенные права доступа и файловые системы большого размера.
  - Предлагает высокую надежность и защиту данных.

- ext4 (Fourth Extended Filesystem)
 Ключевые характеристики:
  - Является одной из самых популярных файловых систем в среде Linux.
  - Активно использует журналирование для повышения надежности.
  - Поддерживает большие файлы и тома.
  - Предоставляет высокую производительность и надежность.

- APFS (Apple File System)
 Ключевые характеристики:
  - Разработана компанией Apple для их операционных систем, таких как macOS, iOS, watchOS и tvOS.
  - Поддерживает криптографическое шифрование, клонирование файлов и снимки файловой системы для быстрого восстановления.
  - Обеспечивает оптимизацию для SSD и флэш-накопителей.

- ZFS (Zettabyte File System)
 Ключевые характеристики:
  - Ориентирована на обеспечение высокой отказоустойчивости и устойчивости к повреждениям данных.
  - Поддерживает расширенные возможности управления данными, такие как снимки, клонирование, восстановление после сбоев и автоматическое исправление ошибок.

Каждая файловая система имеет свои особенности и применение в зависимости от целей использования и требований к надежности и производительности. Понимание особенностей этих файловых систем помогает выбрать наиболее подходящий вариант для конкретного применения.

В файловых системах данные организованы с помощью нескольких ключевых принципов, которые обеспечивают эффективное управление файлами и папками. Давай рассмотрим основные принципы:

1. Иерархическая структура
Файловые системы организованы в виде иерархии, похожей на дерево, в котором узлы представляют папки (каталоги), а листья - файлы. Это организационное устройство облегчает структурирование данных и помогает пользователям легко найти нужные файлы.

2. Индексирование и адресация
Каждый файл в файловой системе имеет свой уникальный адрес или индекс, который обеспечивает быстрый доступ к данным. Это позволяет операционной системе быстро находить и обращаться к файлам, даже когда на диске много других файлов.

3. Метаданные
Метаданные представляют собой информацию о файлах и папках, такую как имя, размер, даты создания и изменения, права доступа и местоположение на диске. Файловая система хранит эти метаданные в специальных областях на носителе данных, что помогает операционной системе управлять файлами и контролировать доступ к ним.

4. Управление свободным пространством
Файловая система отслеживает, какие блоки данных заняты, а какие свободны. Это позволяет осуществлять размещение новых файлов и управлять изменениями в существующих файлах.

5. Журналирование
Некоторые файловые системы поддерживают журналирование, что позволяет вести отслеживание всех изменений, сделанных в файловой системе. Этот метод повышает надежность и целостность файловой системы, так как при сбое операционной системы можно восстановить состояние файловой системы с помощью журнала.

## Квиз

Вопрос 1
Характеристика: Поддержка многих операционных систем
Ответ: Обе файловые системы

И в FAT32, и в NTFS есть поддержка многих операционных систем. Однако, NTFS в основном используется в операционных системах Windows, в то время как FAT32 поддерживается многими операционными системами, включая Windows, macOS и многие дистрибутивы Linux.

Вопрос 2
Характеристика: Подходит для съемных носителей, таких как флэш-накопители, SD-карты
Ответ: FAT32

FAT32 часто используется на съемных устройствах, таких как флэш-накопители и SD-карты, потому что она обладает хорошей совместимостью с различными операционными системами и может быть удобно использована для обмена файлами между разными устройствами.

Вопрос 3
Характеристика: Поддержка файлов большого размера и объемов томов
Ответ: NTFS

NTFS имеет поддержку файлов и объемов томов больших размеров, что делает ее более подходящей для хранения крупных файлов и работы с большими накопителями данных, чем FAT32.

Вопрос 4
Характеристика: Разработана корпорацией Microsoft
Ответ: NTFS

NTFS была разработана корпорацией Microsoft. Она является стандартной файловой системой для операционных систем семейства Windows и предлагает расширенные возможности по сравнению с более старой файловой системой FAT32.

Разберём несколько механизмов файловой системы, чтобы лучше понять как она работает:

- Индексация. Индексация в файловой системе представляет собой механизм организации данных, облегчающий доступ к файлам на диске путем создания структуры данных, которая ускоряет процесс поиска и обращения к файлам.

Принципы работы

1. Создание индексов: При создании или изменении файловой системы, операционная система создает индексы для файлов, содержащие метаданные, такие как имена файлов, их местоположение, время создания, размер и другие атрибуты.
   
2. Ускоренный доступ: Используя эти индексы, операционная система может быстро находить нужные файлы, обращаться к ним, выполнять поиск и фильтрацию, не обязательно просматривая каждый сектор диска в поисках конкретного файла.

3. Поддержка поиска по различным критериям: Индексы позволяют операционной системе выполнять поиск файлов по различным критериям, таким как имя файла, дата создания, тип файла и другие атрибуты, ускоряя процесс обработки пользовательских запросов.

Индексация ускоряет процесс поиска файлов, особенно на больших дисках, что делает доступ к данным более эффективным и удобным. Благодаря индексам, операционная система может извлекать информацию о файлах в соответствии с различными критериями, что увеличивает гибкость в доступе к данным. Индексация также может потреблять дополнительные ресурсы, такие как место на диске для хранения индексов и вычислительные ресурсы для поддержания и обновления этих индексов.

- Размещение файлов. Размещение файлов - это ключевой механизм файловой системы, который определяет, как файлы физически размещаются на диске, чтобы обеспечить эффективное и оптимальное использование пространства и быстрый доступ к данным.

Принципы работы

1. Выделение места на диске: При создании нового файла или при копировании существующего, файловая система должна решить, в каких секторах диска этот файл будет храниться.

2. Обеспечение непрерывности данных: Файловая система должна обеспечить такое размещение файлов, чтобы данные сохранялись непрерывно. Это улучшает производительность, поскольку обеспечивает более быстрый доступ к данным на диске.

3. Эффективное использоание пространства: При размещении файлов файловая система стремится использовать пространство на диске максимально эффективно, чтобы избежать фрагментации и уменьшения производительности.

  Управление свободным пространством. Так же помогает эффективно использовать место на диске. Файловая система отслеживает, какие блоки данных на диске свободны, и ведет учет их доступности для использования новыми файлами или для расширения существующих. В процессе создания, изменения и удаления файлов, дисковая структура может стать фрагментированной, что означает, что файлы распределены в несмежные блоки на диске. Управление свободным пространством включает в себя процессы уплотнения данных, которые целью имеют облегчить доступ и улучшить производительность. Файловая система должна принимать решения о том, какие блоки данных использовать для новых файлов. Это включает в себя аллокацию сквозных блоков для больших файлов, управление индексами для быстрого доступа к свободному пространству и распределение блоков данных эффективным образом. Управление свободным пространством также связано с оптимизацией доступа, включая предвзятый выбор блоков данных для улучшения скорости доступа к файлам и сокращение фрагментации. Эффективное управление свободным пространством важно для производительности файловой системы, так как это обеспечивает оптимальное использование дискового пространства, снижает фрагментацию данных и обеспечивает быстрый доступ к файлам.

Журналирование - это важный механизм, используемый в файловых системах для обеспечения устойчивости и восстановления данных в случае сбоев или ошибок. Вот как это работает:
Журналирование предназначено для отслеживания изменений, которые будут внесены в файловую систему, путем записи этих изменений в специальный журнал. Это позволяет обеспечить целостность файловой системы даже в случае внезапного отключения питания или других сбоев.

Файловая система ведет журнал транзакций, в котором регистрируются все действия, которые будут внесены в файловую систему, такие как создание, изменение или удаление файлов и каталогов. Это происходит до того, как сами изменения будут фактически применены к файловой системе.

В случае сбоя или отказа системы, при повторном запуске операционной системы, восстановление файловой системы может быть выполнено с использованием журнала транзакций. Операционная система может восстановить состояние файловой системы, откатив транзакции, которые не были успешно завершены в момент сбоя.
Журналирование повышает устойчивость файловой системы к сбоям, предотвращая потерю данных или повреждение файловой системы. Хотя журналирование обеспечивает устойчивость данных, иногда косвенно снижает производительность из-за обращений к журналу при каждой операции записи. Однако, этот недостаток компенсируется уровнем надежности и восстановления данных, который предоставляется журналированием.
Некоторые файловые системы, такие как NTFS (используемая в Windows) и ext4 (используемая в Linux), используют журналирование для обеспечения устойчивости и восстановления файловой системы после сбоев.

В целом, журналирование - это важный механизм, который способствует устойчивости и надежности файловой системы, обеспечивая возможность восстановления состояния после сбоев и обеспечивая целостность данных.

Разберём конкретный пример: выключение питания компьютера в процессе сохранения важных данных. Это одна из тех типичных и фрустрирующих ситуаций, когда команда "shutdown -h now" становится настоящим испытанием для наших нервов! Давай разберем, что происходит, когда ты выключаешь компьютер во время сохранения важных данных.
Итак, представь, что ты работаешь над важным документом и решил сохранить его на жесткий диск. Ты нажимаешь "Save" и в этот момент компьютер начинает записывать данные на жесткий диск. Здесь вступает в игру журналирование, о котором мы говорили ранее. Когда файловая система осуществляет запись данных на диск, она делает это с использованием различных механизмов, и журналирование позволяет отслеживать эти операции записи.
Теперь, если ты вдруг выключаешь компьютер в этот момент (будь то намеренно или из-за сбоя питания), важно понимать, что журналирование приходит на помощь. В этой ситуации файловая система обратится к своему журналу, чтобы понять, какие операции записи были выполнены и какие еще предстояли. Она может использовать эту информацию для завершения или отката неполных операций записи, чтобы восстановить целостность файловой системы к более стабильной точке.
Тем не менее, важно понимать, что даже при наличии журналирования не всегда удается избежать потери данных в случае выключения компьютера в процессе сохранения. Это связано с тем, что временное сбои или проблемы с аппаратурой могут создать сложности, даже при наличии журналирования. Поэтому всегда лучше избегать выключения компьютера во время активной записи данных, чтобы минимизировать риск потери информации.
И помни, регулярное создание резервных копий важных данных — это наилучший способ предотвращения потери информации. Так что лучше периодически бэкапить свои файлы, чтобы быть уверенным в безопасности своей информации вне зависимости от ситуации!

# Шифрование в файловых системах

Шифрование в файловых системах представляет собой метод защиты данных путем преобразования их в нечитаемый формат с использованием различных алгоритмов шифрования. Давай рассмотрим различные виды шифрования, их применение, а также преимущества и недостатки.

# Виды шифрования:

1. LUKS (Linux Unified Key Setup):
    - Применение: LUKS представляет собой стандартное средство шифрования для дисков в Linux. Он позволяет зашифровать целый диск или используется для шифрования отдельных разделов.
    - Преимущества: Прост в использовании, поддерживается большинством современных дистрибутивов Linux. Позволяет использовать различные алгоритмы шифрования.
    - Недостатки: Нет возможности изменения пароля без перешифрования всего диска, что может быть неудобно.

2. eCryptFS (Enterprise Cryptographic Filesystem):
    - Применение: eCryptFS предоставляет индивидуальное шифрование для отдельных файлов или каталогов. Это может быть полезно для шифрования конфиденциальных данных на уровне пользователя.
    - Преимущества: Позволяет шифровать отдельные файлы или каталоги. Интегрирован во многие дистрибутивы Linux.
    - Недостатки: Может потреблять больше ресурсов, чем шифрование на уровне диска.

3. dm-crypt предоставляет прозрачное шифрование битового уровня для блочных устройств. Это позволяет зашифровать любое блочное устройство, например, жесткий диск или раздел, без необходимости изменения файловой системы.
    - Применение: Может быть использован для шифрования целых дисков, разделов или даже виртуальных дисков.
    - Преимущества: Потребляет меньше ресурсов, чем некоторые другие методы, позволяет шифровать любые блочные устройства.
    - Недостатки: Управление ключами и паролями может быть сложным при большом количестве зашифрованных устройств.
  
Шифрование в файловых системах Linux предоставляет надежный способ защиты данных от несанкционированного доступа. Выбор конкретного метода шифрования должен зависеть от конкретных потребностей безопасности и требований вашей системы.

# Сжатие данных в файловых системах

В файловых системах сжатие данных является важным инструментом для уменьшения объема занимаемого дискового пространства. На практике существует несколько методов сжатия, которые могут быть использованы в различных сценариях. Давай рассмотрим основные методы сжатия данных в файловых системах Linux.

# Алгоритмы сжатия

1. gzip
gzip - это один из самых распространенных алгоритмов сжатия в Linux. Он обеспечивает хорошее сжатие и отличную скорость работы.

Пример использования:
```
gzip имя_файла
```

2. bzip2
bzip2 - обеспечивает более высокий уровень сжатия по сравнению с gzip, но работает медленнее.

Пример использования:
```
bzip2 имя_файла
```

3. xz
xz - обеспечивает еще более высокий уровень сжатия, но работает еще медленнее, чем bzip2.

Пример использования:
```
xz имя_файла
```

4. Прозрачное сжатие данных
Некоторые современные файловые системы, такие как Btrfs и ZFS, предоставляют встроенную поддержку прозрачного сжатия данных. Это означает, что данные автоматически сжимаются при записи на диск и распаковываются при чтении, не требуя дополнительных действий от пользователя.

Пример использования сжатия данных в Btrfs:

 Создание Btrfs тома с использованием сжатия
 ```
mkfs.btrfs -m single -d single -f -L СжатыйТом /dev/sdX
```
 Применение сжатия данных

1. Сжатие архивов: Для создания архивов сжатия данных для резервного копирования или передачи через сеть.
2. Сжатие логов: Для экономии места и облегчения анализа.
3. Сжатие виртуальных жестких дисков: Для уменьшения размера виртуальных машин и экономии дискового пространства.

Преимущества:
- Экономия места: Сжатие данных позволяет эффективнее использовать дисковое пространство.
- Уменьшение нагрузки на дисковую подсистему: Менее данных означает быстрый доступ к ним.

Недостатки:
- Потребление процессорного времени: Сжатие и разжатие данных требуют вычислительных ресурсов.
- Потеря производительности при работе с сжатыми данными: В зависимости от типа данных, некоторые операции могут занимать больше времени.

Сжатие данных в файловых системах Linux представляет собой важный инструмент для управления дисковым пространством. Выбор конкретного метода сжатия будет зависеть от ваших потребностей по скорости, уровню сжатия и использования ресурсов системы.

Давай создадим эффективную структуру каталогов для их хранения, учитывая размеры файлов и частоту доступа.

Для начала, давай подумаем о том, какие типы данных у нас есть. Мы можем разделить данные на несколько основных категорий, такие как анимационные фильмы, сериалы, фоновые изображения, звуковые эффекты и т.д.

Далее, у нас есть несколько вариантов организации данных. Мы можем использовать структуру каталогов, основанную на частоте доступа к данным, или же на типе данных (например, фильмы, изображения, звуки).

Организация на основе типа данных:
```
- /Фильмы
    - /Полнометражные
    - /Короткометражные
- /Сериалы
- /Изображения
    - /Фоны
    - /Персонажи
- /Звуки
    - /Диалоги
    - /Музыка
- /Другие_данные
```

Организация на основе частоты доступа:
```
- /Часто_используемые
    - /Активные_проекты
    - /Популярные_мультфильмы
- /Редко_используемые
    - /Старые_проекты
    - /Архив
```

Мы также можем комбинировать эти методы, создавая структуру каталогов, которая учитывает и тип данных, и частоту доступа. Например, создавая основную структуру на основе типа данных, а затем внутри каждой категории имея подкаталоги для часто и редко используемых данных.

Например:
```
- /Фильмы
    - /Полнометражные
        - /Часто_используемые
        - /Редко_используемые
    - /Короткометражные
        - /Часто_используемые
        - /Редко_используемые
- /Сериалы
    - /Часто_используемые
    - /Редко_используемые
- /Изображения
    - /Фоны
        - /Часто_используемые
        - /Редко_используемые
    - /Персонажи
        - /Часто_используемые
- /Звуки
    - /Диалоги
        - /Часто_используемые
        - /Редко_используемые
    - /Музыка
- /Другие_данные

```

Таким образом, мы создаем более гибкую структуру, которая может учитывать и тип данных, и частоту доступа.

## Квиз

1. Какая функция НЕ относится к файловой системе NTFS (New Technology File System) в операционной системе Windows?

a) Журналирование  
b) Компрессия данных  
c) Безопасный режим для исполнения файлов  
d) Шифрование всего диска  

Правильный ответ: c) Безопасный режим для исполнения файлов  
Объяснение: Все варианты, кроме c, относятся к функциям NTFS. Журналирование, компрессия данных и шифрование всего диска - это стандартные функции NTFS, обеспечивающие повышенную надежность, управление пространством на диске и защиту данных. "Безопасный режим для исполнения файлов" относится к другим аспектам системы, но не связан с файловой системой NTFS.

2. Какой из следующих алгоритмов сжатия данных наиболее эффективен, обеспечивая высокую степень сжатия?

a) gzip  
b) bzip2  
c) xz  
d) zlib  

Правильный ответ: c) xz  
Объяснение: Алгоритм сжатия данных xz обеспечивает наиболее высокую степень сжатия по сравнению с gzip, bzip2 и zlib. Хотя другие алгоритмы также эффективны, xz обычно обеспечивает более высокий уровень сжатия за счет более сложного алгоритма сжатия данных.
3. Какая из файловых систем является распространенной в операционной системе Linux?
   - a) NTFS
   - b) FAT32
   - c) ext4
   - d) APFS
   - Правильный ответ: c) ext4. Объяснение: Файловая система ext4 является одной из наиболее широко используемых файловых систем в операционной системе Linux из-за своей производительности и надежности.

4. Какие характеристики файловой системы важны для масштабируемости?
   - a) Производительность, надежность
   - b) Поддержка функций, совместимость
   - c) Совместимость, ограничения по размеру файлов и разделов
   - d) Надежность, масштабируемость
   - Правильный ответ: d) Надежность, масштабируемость. Объяснение: Для масштабируемости важны как надежность хранения данных, так и способность масштабирования для больших объемов данных.

Мы разобрались в основных принципах файловой системы, изучили важные механизмы, такие как управление свободным пространством, журналирование, а также узнали об индексировании и метаданных. Затем мы погрузились в область шифрования в файловых системах, рассмотрели различные виды шифрования, их применение и особенности, обсудили инструменты, такие как LUKS, eCryptFS и dm-crypt.
И наконец, мы обсудили сжатие данных в файловых системах, изучили различные методы сжатия, такие как gzip, bzip2, xz, и поняли, как сжатие может быть использовано для оптимизации использования дискового пространства.