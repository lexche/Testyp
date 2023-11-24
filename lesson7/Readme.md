Представьте архитектуру операционной системы, где множество различных процессов и пользователей одновременно запрашивают доступ к ресурсам. Как ОС обеспечивает безопасность и изоляцию данных, защищая их от несанкционированного доступа или влияния других процессов?

Операционная система защищает данные разных пользователей и процессов (права пользователей). Ещё она может добавлять дополнительные механизмы защиты.

В Linux каждый пользователь имеет свои роли и привилегии, которые определяют, что он или она может делать в системе. Поговорим сначала об обычном пользователе.

- Обычный пользователь

Обычный пользователь - это учетная запись с ограниченными привилегиями. Он может запускать большинство программ, создавать, удалять и изменять свои собственные файлы, но не имеет права вносить изменения в системные файлы или устанавливать программное обеспечение для всей системы. Таким образом, обычный пользователь обеспечивает безопасное средство разделения и управления ресурсами.

- Привилегированный администратор (root)

Привилегированный администратор, также известный как root, обладает полным контролем над системой. Он имеет права на выполнение любых действий, включая установку и удаление программ, управление пользователями, изменение конфигурации системы и многое другое. Root - это суперпользователь с абсолютными привилегиями в системе.

Роли обычного пользователя и привилегированного админа

1. Обычный пользователь: С точки зрения безопасности обычные пользователи представляют минимальный уровень доступа к системе, что помогает предотвращать ошибки или злонамеренные действия, которые могут повредить операционную систему. Обычные пользователи не имеют доступа к системным файлам и настройкам, что защищает систему от непреднамеренного повреждения.

2. Привилегированный администратор: Root-доступ позволяет управлять системой и решать задачи, требующие высоких привилегий, такие как установка программного обеспечения, настройка системных параметров и обслуживание системы. Однако он также представляет потенциальную угрозу безопасности, поскольку любые ошибки или злонамеренные действия, совершаемые от имени root, могут нанести серьезный ущерб системе.

Роли обычного пользователя и привилегированного админа представляют разные уровни доступа и ответственности в системе Linux.

Системы управления доступом (СУД) представляют собой ключевые аспекты безопасности операционных систем. Рассмотрим DAC, MAC и RBAC, а также их внедрение в архитектуру ОС .

- Дискреционный контроль доступа (DAC)

DAC определяет доступ к ресурсам (файлам, устройствам) на основе прав владельца, группы и остальных пользователей. В Linux каждый файл имеет атрибуты владельца, группы и остальных пользователей, и их сочетание определяет, кто имеет доступ к файлу.

 Внедрение в Linux:
DAC встроен в ядро Linux и реализуется с использованием POSIX-совместимой модели прав доступа к файлам. Когда файл создается, система определяет права доступа на основе текущих настроек масок создания файлов для пользователя и текущей umask.

- Мандатный контроль доступа (MAC)

MAC предоставляет более гранулированный контроль доступа, используя политики безопасности, определяющие, кто имеет право видеть и модифицировать определенные ресурсы. Примерами MAC являются SELinux (Security-Enhanced Linux) и AppArmor.

 Внедрение в Linux:
В Linux MAC встроен в ядро, но требует настройки и активации. Например, для использования SELinux необходимы специальные метки безопасности файлов и настроенные политики для контроля доступа.

- Ролевой контроль доступа (RBAC)

RBAC представляет собой механизм, в котором доступ к ресурсам определяется на основе ролей, а не прямых идентификаторов пользователей. 

Внедрение в Linux:
В Linux, RBAC может быть реализован с использованием инструментов, таких как Role-Based Access Control (RBAC) на основе SELinux, где администраторы могут назначать роли и связанные с ними разрешения.

Внедрение систем управления доступом в архитектуру ОС Linux - это важный аспект обеспечения безопасности. Оно позволяет создавать более защищенные среды, контролировать доступ пользователей к ресурсам и предотвращать несанкционированный доступ к конфиденциальным данным.

Системы управления доступом обеспечивают разностороннюю защиту, и их внедрение в Linux помогает улучшить безопасность и гарантировать выполнение бизнес-требований по безопасности.

## Квиз

Рассмотрим сценарии настройки ОС для различных типов пользователей. Выберите правильный ответ.

 1. Для обычного пользователя

 Доступ к собственным файлам и каталогам:
   - Вариант A: Ограниченный доступ только к собственным файлам и каталогам пользователя.
   - Вариант B: Полный доступ ко всем файлам и каталогам в системе.

Правильный вариант: Вариант A. Обычному пользователю следует иметь ограниченный доступ только к своим собственным файлам и каталогам, чтобы обеспечить безопасность и конфиденциальность данных.

2. Для системного администратора

  Суперпользовательские привилегии:
   - Вариант A: Предоставление суперпользовательских привилегий для выполнения задач, требующих высоких привилегий.
   - Вариант B: Ограниченные привилегии, схожие с обычным пользователем, для обеспечения безопасности.

Правильный вариант: Вариант A. Системный администратор должен иметь полный доступ ко всем системным ресурсам для выполнения административных задач, поэтому суперпользовательские привилегии обязательны.

3. Для гостевого пользователя

   Ограниченный доступ и изоляция:
   - Вариант A: Ограниченный доступ к определенным ресурсам и изоляция от системных файлов и настроек.
   - Вариант B: Полный доступ ко всем ресурсам с теми же возможностями, что и у обычных пользователей.

Правильный вариант: Вариант A. Гостевому пользователю следует предоставить ограниченный доступ к ресурсам и обеспечить изоляцию от системных файлов и настроек для обеспечения безопасности и сохранности системы.

4. Для разработчика

Доступ к системным инструментам и ресурсам:
   - Вариант A: Полномочия для доступа к разработческим ресурсам и инструментам.
   - Вариант B: Ограниченный доступ без возможности управления системными инструментами.

Правильный вариант: Вариант A. Разработчику необходим доступ к системным инструментам и ресурсам для разработки программного обеспечения, поэтому важно предоставить соответствующие права доступа.