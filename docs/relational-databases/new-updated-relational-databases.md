---
title: Обновлено — документы по реляционным базам данных | Документация Майкрософт
description: Отображение фрагментов обновленного содержимого для последних изменений в документации по реляционным базам данных.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: conceptual
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: relational-databases
ms.date: 04/28/2018
ms.openlocfilehash: 4f962279eb30e15b395f96417cc5e03aa1dbcfad
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087776"
---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Новые и недавно обновленные статьи — документы по реляционным базам данных



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Даты обновлений:* &nbsp; **02.03.2018**&nbsp;–&nbsp;**28.04.2018**
- *Предметная область:* &nbsp; **Реляционные базы данных**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Соединения (SQL Server)](performance/joins.md)
2. [Вложенные запросы (SQL Server)](performance/subqueries.md)
3. [Настройка базы данных распространителя репликации в группе доступности AlwaysOn](replication/configure-distribution-availability-group.md)
4. [Обнаружение и классификация данных SQL](security/sql-data-discovery-and-classification.md)
5. [Руководство по блокировке и управлению версиями строк транзакций](sql-server-transaction-locking-and-row-versioning-guide.md)
6. [sys.dm_os_job_object (база данных SQL Azure)](system-dynamic-management-views/sys-dm-os-job-object-transact-sql.md)
7. [Системные хранимые процедуры Filestream и FileTable (Transact-SQL)](system-stored-procedures/filestream-and-filetable-system-stored-procedures.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Использование файла форматирования для пропуска столбца таблицы (SQL Server)](#TitleNum_1)
2. [Данные JSON в SQL Server](#TitleNum_2)
3. [Руководство по архитектуре обработки запросов](#TitleNum_3)
4. [Учебник. Подготовка SQL Server для репликации — издатель, распространитель, подписчик](#TitleNum_4)
5. [Учебник. Настройка репликации между двумя полностью подключенными серверами (репликация транзакций)](#TitleNum_5)
6. [Учебник. Настройка репликации между сервером и мобильными клиентами (репликация слиянием)](#TitleNum_6)
7. [Запросы с полнотекстовым поиском](#TitleNum_7)
8. [Прозрачное шифрование с поддержкой использования собственных ключей для хранилища и базы данных SQL Azure](#TitleNum_8)
9. [Включение прозрачного шифрования данных с использованием собственного ключа из Azure Key Vault с помощью PowerShell и CLI](#TitleNum_9)
10. [Отслеживание измененных данных (SQL Server)](#TitleNum_10)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-use-a-format-file-to-skip-a-table-column-sql-serverimport-exportuse-a-format-file-to-skip-a-table-column-sql-servermd"></a>1. &nbsp; [Использование файла форматирования для пропуска столбца таблицы (SQL Server)](import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)

*Обновлено: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 221.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 167916d79c5de1e7f13990cb7acc41ceb541b9a7 cb92eb201292294e3397879c98f353fba45f1c1c  (PR=0  ,  Filename=use-a-format-file-to-skip-a-table-column-sql-server.md  ,  Dirpath=docs\relational-databases\import-export\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**Применение инструкции OPENROWSET(BULK...)**


Чтобы использовать XML-файл форматирования для пропуска столбца таблицы с помощью `OPENROWSET(BULK...)`, предоставьте в явном виде следующий список столбцов в списке выбора и в целевой таблице, как показано ниже:

```
    INSERT ...<column_list> SELECT <column_list> FROM OPENROWSET(BULK...)
```

В следующем примере используется поставщик массового набора строк `OPENROWSET` и файл форматирования `myTestSkipCol2.xml` . В примере выполняется массовый импорт файла данных `myTestSkipCol2.dat` в таблицу `myTestSkipCol` . Инструкция, в соответствии с требованиями, содержит явный список столбцов в списке выбора, а также в целевой таблице.

Выполните в SSMS следующий код. Обновите пути файловой системы к файлам образцов на вашем компьютере.

```
USE WideWorldImporters;
GO
INSERT INTO myTestSkipCol
  (Col1,Col3)
    SELECT Col1,Col3
      FROM  OPENROWSET(BULK  'C:\myTestSkipCol2.Dat',
      FORMATFILE='C:\myTestSkipCol2.Xml'
       ) as t1 ;
GO
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-json-data-in-sql-serverjsonjson-data-sql-servermd"></a>2. &nbsp; [Данные JSON в SQL Server](json/json-data-sql-server.md)

*Обновлено: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_1) | [Далее](#TitleNum_3))

<!-- Source markdown line 145.  ms.author= "jovanpop".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 19e276637a463b412f2c29a84f9fb7d0b0f5fcc5 e2f2e8b4732779b3f24561cc0c4da3a958f4edbb  (PR=0  ,  Filename=json-data-sql-server.md  ,  Dirpath=docs\relational-databases\json\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



Документы JSON могут содержать вложенные элементы и иерархические данные, которые невозможно напрямую сопоставить со стандартными реляционными столбцами. В этом случае можно выполнить сведение иерархии JSON посредством соединения родительской сущности с вложенными массивами.

В следующем примере второй объект в массиве содержит вложенный массив, представляющий навыки сотрудника. Каждый вложенный объект может быть проанализирован с помощью дополнительных вызовов функции `OPENJSON`:

```
DECLARE @json NVARCHAR(MAX)
SET @json =
N'[
       { "id" : 2,"info": { "name": "John", "surname": "Smith" }, "age": 25 },
       { "id" : 5,"info": { "name": "Jane", "surname": "Smith", "skills": ["SQL", "C#", "Azure"] }, "dob": "2005-11-04T12:00:00" }
 ]'

SELECT *
FROM OPENJSON(@json)
  WITH (id int 'strict $.id',
        firstName nvarchar(50) '$.info.name', lastName nvarchar(50) '$.info.surname',
        age int, dateOfBirth datetime2 '$.dob',
    skills nvarchar(max) '$.skills' as json)
    outer apply openjson( a.skills )
                     with ( skill nvarchar(8) '$' ) as b
```
Массив **skills** возвращается в первой функции `OPENJSON` в качестве исходного фрагмента текста JSON и передается в другую функцию `OPENJSON` с использованием оператора `APPLY`. Вторая функция `OPENJSON` анализирует массив JSON и возвращает строковые значения в виде единого набора строк столбцов, который будет соединен с результатами первой функции `OPENJSON`.
Результат этого запроса показан в следующей таблице:

**Результаты**

|идентификатор|firstName|lastName|age|dateOfBirth|skill|
|--------|---------------|--------------|---------|-----------------|----------|
|2|Джон|Смит|25|||
|5|Джейн|Смит||2005-11-04T12:00:00|SQL|
|5|Джейн|Смит||2005-11-04T12:00:00|C#|
|5|Джейн|Смит||2005-11-04T12:00:00|Azure|

Функция `OUTER APPLY OPENJSON` соединит сущности первого уровня с вложенным массивом и вернет преобразованный в плоскую структуру набор результатов. Из-за выполнения операции JOIN вторая строка будет повторяться для каждого навыка.




&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-query-processing-architecture-guidequery-processing-architecture-guidemd"></a>3. &nbsp; [Руководство по архитектуре обработки запросов](query-processing-architecture-guide.md)

*Обновлено: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_2) | [Далее](#TitleNum_4))

<!-- Source markdown line 34.  ms.author= "jroth".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 96d91b39acdb2f32aaff323e374e92d6f229d241 2c1d2f8585632ada174388399782dc3ed2721dba  (PR=0  ,  Filename=query-processing-architecture-guide.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**Приоритет логических операторов**


При использовании в инструкции нескольких логических операторов первым вычисляется `NOT`, затем `AND` и, наконец, `OR`. Арифметические и побитовые операторы выполняются до логических. Дополнительные сведения см. в разделе [Приоритет операторов].

В приведенном ниже примере условие цвета относится к модели продукта 21, но не к модели продукта 20, так как оператора `AND` имеет приоритет над оператором `OR`.

```
SELECT ProductID, ProductModelID
FROM Production.Product
WHERE ProductModelID = 20 OR ProductModelID = 21
  AND Color = 'Red';
GO
```

Можно изменить смысл запроса, добавляя скобки, чтобы добиться вычисления `OR` сначала. В приведенном ниже запросе будут найдены модели 20 и 21 красного цвета.

```
SELECT ProductID, ProductModelID
FROM Production.Product
WHERE (ProductModelID = 20 OR ProductModelID = 21)
  AND Color = 'Red';
GO
```

С помощью скобок, даже если они не требуются, можно улучшить читаемость запросов и уменьшить вероятность совершения незаметной ошибки из-за приоритета операторов. Использование скобок практически не влияет на производительность. Следующий пример более понятен, чем исходный, хотя синтаксически они равноправны.

```
SELECT ProductID, ProductModelID
FROM Production.Product
WHERE ProductModelID = 20 OR (ProductModelID = 21
  AND Color = 'Red');
GO
```




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-tutorial-prepare-sql-server-for-replication---publisher-distributor-subscriberreplicationtutorial-preparing-the-server-for-replicationmd"></a>4. &nbsp; [Учебник. Подготовка SQL Server к репликации — издатель, распространитель, подписчик](replication/tutorial-preparing-the-server-for-replication.md)

*Обновлено: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_3) | [Далее](#TitleNum_5))

<!-- Source markdown line 56.  ms.author= "mathoma".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 6e5caedacff193ce79bdd98708ae1b9dc91f0a8f 9f7af4d3f8b1cffd048db2a5b29fc9e6013f5ed2  (PR=0  ,  Filename=tutorial-preparing-the-server-for-replication.md  ,  Dirpath=docs\relational-databases\replication\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



- Установите [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Установите выпуск [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Скачайте [образцы баз данных AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Инструкции по восстановлению базы данных из копии в среде SSMS см. в разделе [Восстановление базы данных](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).

>[!NOTE]
> - Репликация не поддерживается на серверах SQL Server, которые отличаются друг от друга более чем на две версии. Дополнительные сведения см. в разделе [Поддерживаемые версии SQL в топологии репликации](https://blogs.msdn.microsoft.com/repltalk/2016/08/12/suppported-sql-server-versions-in-replication-topology/).
> - В среде *{укажите_включенный_контент}* необходимо подключиться к издателю и подписчику по имени для входа, относящегося к предопределенной роли сервера **sysadmin**. Дополнительные сведения о роли sysadmin см. в разделе [Роли уровня сервера](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/server-level-roles).


**Предполагаемое время для выполнения заданий данного учебника: 30 минут**

**Создание учетных записей Windows для репликации**

В этом разделе будут созданы учетные записи Windows для запуска агентов репликации. На локальном сервере будут созданы отдельные учетные записи Windows для следующих агентов:

|Агент|Местоположение|Имя учетной записи|
|---------|------------|----------------|
|агент моментальных снимков|Издатель|<*имя_компьютера*>\repl_snapshot|



&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-tutorial-configure-replication-between-two-fully-connected-servers-transactionalreplicationtutorial-replicating-data-between-continuously-connected-serversmd"></a>5. &nbsp; [Учебник. Настройка репликации между двумя полностью подключенными серверами (репликация транзакций)](replication/tutorial-replicating-data-between-continuously-connected-servers.md)

*Обновлено: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_4) | [Далее](#TitleNum_6))

<!-- Source markdown line 162.  ms.author= "mathoma".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0d74f984d0ffc01cce0376837e6d94df3c5654d7 4ecf4d724286130927dd43687d6845059af6f9b7  (PR=0  ,  Filename=tutorial-replicating-data-between-continuously-connected-servers.md  ,  Dirpath=docs\relational-databases\replication\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**Создание подписки на публикацию транзакций**

В этом разделе описывается добавление подписчика к ранее созданной публикации. В этом учебнике используется удаленный подписчик (NODE2\SQL2016), однако при необходимости подписку для издателя можно также добавить локально.

**Создание подписки**


1.  Подключитесь к издателю в среде *{укажите_включенный_контент}*, а затем разверните узел сервера и папку **Репликация** .

2.  В папке **Локальные публикации** щелкните правой кнопкой мыши публикацию **AdvWorksProductTrans** и выберите команду **Создать подписку**.  Откроется мастер создания подписки:

    Создать подписку

3.  На странице "Публикация" выберите публикацию **AdvWorksProductTrans** и нажмите кнопку **Далее**:

    Выбор издателя транзакций

4.  На странице "Расположение агента распространителя" установите флажок **Выполнять все агенты на распространителе** и нажмите кнопку **Далее**.  Дополнительные сведения о подписках см. в статье [Подписка на публикации](https://docs.microsoft.com/sql/relational-databases/replication/subscribe-to-publications):

    Выполнение агентов на распространителе

5.  На странице "Подписчики", если имя экземпляра подписчика не отображается, выберите пункт **Добавить подписчик**, а затем выберите **Добавить подписчик SQL Server** из раскрывающегося списка. Откроется диалоговое окно **Соединение с сервером**. Введите имя экземпляра подписчика, а затем выберите **Подключиться**.



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-tutorial-configure-replication-between-a-server-and-mobile-clients-mergereplicationtutorial-replicating-data-with-mobile-clientsmd"></a>6. &nbsp; [Учебник. Настройка репликации между сервером и мобильными клиентами (репликация слиянием)](replication/tutorial-replicating-data-with-mobile-clients.md)

*Обновлено: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_5) | [Далее](#TitleNum_7))

<!-- Source markdown line 93.  ms.author= "mathoma".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0eed78dfe83c88358c030539a2b25d11ef5ec2d3 79b2a3f32c940fede94b11ad2a3ef8a00b911a39  (PR=0  ,  Filename=tutorial-replicating-data-with-mobile-clients.md  ,  Dirpath=docs\relational-databases\replication\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



Таблица Employee содержит столбец (OrganizationNode) с типом данных hierarchyid, который поддерживается для репликации только в SQL 2017. Если вы используете сборку ниже версии SQL 2017, в нижней части экрана появится сообщение с уведомлением о риске потери данных при использовании этого столбца для двусторонней репликации. В рамках этого учебника данное сообщение можно игнорировать. Тем не менее, если вы не используете поддерживаемую сборку в рабочей среде, этот тип данных не должен участвовать в репликации. Дополнительные сведения о репликации типа данных hierarchyid см. в разделе [Использование столбцов Hierarchyid в репликации](https://docs.microsoft.com/sql/t-sql/data-types/hierarchyid-data-type-method-reference#using-hierarchyid-columns-in-replicated-tables)


-  На странице "Фильтрация строк таблицы" выберите **Добавить**, а затем щелкните **Добавить фильтр**.

-  В диалоговом окне **Добавить фильтр** выберите **Employee (HumanResources)** в поле **Выбрать таблицу для фильтрации**. Щелкните столбец **LoginID**, щелкните стрелку вправо, чтобы добавить столбец в предложение WHERE фильтрующего запроса, и измените предложение WHERE следующим образом:

    ```
    WHERE [LoginID] = HOST_NAME()
    ```

    A. Щелкните элемент **Строка из этой таблицы будет отправлена только одной подписке** и нажмите кнопку **ОК**:

    Добавление фильтра



- На странице **Фильтрация строк таблицы** выберите **Employee (Human Resources)**, нажмите **Добавить**, а затем **Добавить соединение для расширения выбранного фильтра**.

    A. В диалоговом окне **Добавление соединения** выберите **Sales.SalesOrderHeader** в поле **Соединяемая таблица**. Выберите **Записать инструкцию соединения вручную** и завершите инструкцию соединения следующим образом:



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-query-with-full-text-searchsearchquery-with-full-text-searchmd"></a>7. &nbsp; [Запрос с полнотекстовым поиском](search/query-with-full-text-search.md)

*Обновлено: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_6) | [Далее](#TitleNum_8))

<!-- Source markdown line 247.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5ec67b56aa0a6eadadbcfa8b73b6726e75eca2bb 4eb108b202d3dd035a312bac7872cf02bcf31cfa  (PR=0  ,  Filename=query-with-full-text-search.md  ,  Dirpath=docs\relational-databases\search\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**Дополнительные сведения о создании условий поиска**


*Словоформы* — это глаголы в различных временах и лицах или существительные в формах единственного или множественного числа.

Примером такого поиска может служить поиск словоформ слова "водить". Если разные строки таблицы содержат слова "водить", "водит", "водят", "водил" и "водите", все они войдут в результирующий набор, потому что каждое из этих слов можно образовать флективным способом от слова "водить".

Запросы [FREETEXT] и [FREETEXTTABLE] по умолчанию ищут словоформы всех указанных слов. Запросы [CONTAINS] и [CONTAINSTABLE] поддерживают необязательный аргумент `INFLECTIONAL`.

**Поиск синонимов конкретного слова**


В *тезаурусе* определяются пользовательские синонимы терминов. Дополнительные сведения о файлах тезауруса см. в статье [Настройка файлов тезауруса для полнотекстового поиска и управление ими].

Например, если в тезаурусе есть запись "{машина, автомобиль, грузовик, фургон}", можно искать синонимическую форму слова "машина". В результирующий набор войдут все строки таблицы, содержащие слова "автомобиль", "грузовик", "фургон" или "машина", потому что каждое из этих слов входит в состав расширяющего набора синонимов, содержащего и слово "машина".

По умолчанию тезаурус используется в запросах [FREETEXT] и [FREETEXTTABLE]. Запросы [CONTAINS] и [CONTAINSTABLE] поддерживают необязательный аргумент `THESAURUS`.



&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-transparent-data-encryption-with-bring-your-own-key-support-for-azure-sql-database-and-data-warehousesecurityencryptiontransparent-data-encryption-byok-azure-sqlmd"></a>8. &nbsp; [Прозрачное шифрование с поддержкой использования собственных ключей для хранилища и базы данных SQL Azure](security/encryption/transparent-data-encryption-byok-azure-sql.md)

*Обновлено: 24.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_7) | [Далее](#TitleNum_9))

<!-- Source markdown line 110.  ms.author= "aliceku".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9527658848d430bf0148be84474a75b232cbd112 70ed2a129c580962384f808e8526673957f00d2c  (PR=5662  ,  Filename=transparent-data-encryption-byok-azure-sql.md  ,  Dirpath=docs\relational-databases\security\encryption\  ,  MergeCommitSha40=91a9c812739a1c9a6ec9e7b8cda71ee1f5adae3d) -->



**Настройка географического аварийного восстановления с использованием Azure Key Vault**


Чтобы обеспечить высокую доступность средств защиты TDE для зашифрованных баз данных, необходимо настроить избыточные Azure Key Vault на основе существующих групп отработки отказа или активных экземпляров копий георепликации базы данных SQL.  Каждому геореплицированному серверу требуется отдельное хранилище ключей, которое должно находиться в том же регионе Azure, что и сервер. Если база данных-источник станет недоступной из-за сбоя в одном регионе и активации отработки отказа, база данных-получатель сможет использовать вторичное хранилище ключей.

Для геореплицированных баз данных SQL Azure требуется следующая конфигурация Azure Key Vault:
- Одна база данных-источник с хранилищем ключей в регионе, а также одна база данных-получатель с хранилищем ключей в регионе.
- Обязательно наличие как минимум одной базы данных-получателя (всего поддерживается до четырех таких баз).
- Создание цепочек баз данных, являющихся получателями баз данных-получателей, не поддерживается.

В следующем разделе действия по настройке и конфигурации будут описаны более подробно.

**Действия по конфигурации Azure Key Vault**


- Установите [PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps?view=azurermps-5.6.0)
- Создайте два хранилища Azure Key Vault в двух разных регионах, используя [PowerShell для включения свойства "soft-delete"](https://docs.microsoft.com/azure/key-vault/key-vault-soft-delete-powershell) хранилищ ключей (этот параметр сейчас недоступен на портале Azure Key Vault, но по-прежнему является обязательным для SQL).
- Для работы функций резервного копирования и восстановления ключей оба хранилища ключей Azure Key Vault должны быть расположены в двух регионах, доступных в одном географическом регионе Azure.  Если вам требуется, чтобы два хранилища ключей располагались в разных географических регионах в соответствии с требованиями к георепликации SQL, используйте [процесс BYOK](https://docs.microsoft.com/azure/key-vault/key-vault-hsm-protected-keys), который позволяет импортировать ключи из локального аппаратного модуля безопасности.



&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-powershell-and-cli-enable-transparent-data-encryption-using-your-own-key-from-azure-key-vaultsecurityencryptiontransparent-data-encryption-byok-azure-sql-configuremd"></a>9. &nbsp; [Включение прозрачного шифрования данных с использованием собственного ключа из Azure Key Vault с помощью PowerShell и CLI](security/encryption/transparent-data-encryption-byok-azure-sql-configure.md)

*Обновлено: 24.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_8) | [Далее](#TitleNum_10))

<!-- Source markdown line 196.  ms.author= "aliceku".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a0e00f5701d9a493f503a477c69097ce65aba174 721e8fb856a55ee1e8e9e7fc06036a03adab647b  (PR=5662  ,  Filename=transparent-data-encryption-byok-azure-sql-configure.md  ,  Dirpath=docs\relational-databases\security\encryption\  ,  MergeCommitSha40=91a9c812739a1c9a6ec9e7b8cda71ee1f5adae3d) -->



**Необходимые условия для использования CLI**


- Требуется подписка Azure и права администратора этой подписки.
- [Рекомендуется, но необязательно] Наличие аппаратного модуля безопасности (HSM) или локального хранилища ключей для создания локальной копии материала ключа средства защиты TDE.
- Интерфейс командной строки версии 2.0 или более поздней. Чтобы установить последнюю версию и подключиться к подписке Azure, см. статью [Установка и настройка кроссплатформенного интерфейса командной строки Azure 2.0](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest).
- Созданные Azure Key Vault и ключ для TDE.
   - [Управление Key Vault с помощью CLI 2.0](https://docs.microsoft.com/azure/key-vault/key-vault-manage-with-cli2)
   - [Инструкции по использованию аппаратного модуля безопасности (HSM) и хранилища Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-get-started#a-idhsmaif-you-want-to-use-a-hardware-security-module-hsm)
 - Хранилище ключей, используемое для прозрачного шифрования данных, должно поддерживать следующее свойство:
   - [обратимое удаление](https://docs.microsoft.com/azure/key-vault/key-vault-ovw-soft-delete).
   - [Как использовать обратимое удаление в Key Vault с помощью интерфейса командной строки](https://docs.microsoft.com/azure/key-vault/key-vault-soft-delete-cli)
- Ключ, используемый для прозрачного шифрования данных, должен иметь следующие характеристики:
   - быть бессрочным;
   - не быть отключенным;
   - иметь возможность выполнять операции *получения*, *упаковки ключа*, *распаковки ключа*.

**Шаг. Создание сервера и назначение ему удостоверения Azure Active Directory**

      cli
      # create server (with identity) and database



&nbsp;

&nbsp;

---

<a name="TitleNum_10"/>

### <a name="10-nbsp-about-change-data-capture-sql-servertrack-changesabout-change-data-capture-sql-servermd"></a>10. &nbsp; [Об отслеживании измененных данных (SQL Server)](track-changes/about-change-data-capture-sql-server.md)

*Обновлено: 17.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_9))

<!-- Source markdown line 112.  ms.author= "jroth".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 588bff652adefd719e799e9777a416b70184c5f8 77ebdbb1b98b24054d5c5afbb3f1d40e94d1e6bc  (PR=5574  ,  Filename=about-change-data-capture-sql-server.md  ,  Dirpath=docs\relational-databases\track-changes\  ,  MergeCommitSha40=bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68) -->



**Различия в работе с параметрами сортировки баз данных и таблиц**


Важно учитывать различия в параметрах сортировки между базой данных и столбцами таблицы, настроенных для отслеживания измененных данных. При отслеживании измененных данных используется промежуточное хранилище для заполнения побочных таблиц. Если таблица содержит столбцы типа CHAR или VARCHAR с параметрами сортировки, которые отличаются от параметров сортировки в базе данных, а также если в этих столбцах хранятся символы, не входящие в набор ASCII (например, двухбайтовые символы DBCS), технология отслеживания измененных данных не всегда будет сохранять измененные данные в соответствии с данными в базовых таблицах. Это связано с тем, что с переменными промежуточного хранилища не связаны параметры сортировки.

Чтобы обеспечить согласованность отслеживания измененных данных с базовыми таблицами, следует применять один из приведенных ниже подходов:

- Используйте тип данных NCHAR и NVARCHAR для столбцов, содержащих данные, не относящиеся к набору ASCII.

- Также можно использовать одинаковые параметры сортировки для столбцов и для базы данных.

Например, если в базе данных используются параметры сортировки SQL_Latin1_General_CP1_CI_AS, можно использовать следующую таблицу:

```
CREATE TABLE T1(
     C1 INT PRIMARY KEY,
     C2 VARCHAR(10) collate Chinese_PRC_CI_AI)
```

Технология отслеживания измененных данных может не получать двоичные данные для столбца C2, поскольку он использует другие параметры сортировки (Chinese_PRC_CI_AI). Чтобы избежать этой проблемы, используйте тип NVARCHAR:

```
CREATE TABLE T1(
     C1 INT PRIMARY KEY,
     C2 NVARCHAR(10) collate Chinese_PRC_CI_AI --Unicode data type, CDC works well with this data type)
```







## <a name="similar-articles-about-new-or-updated-articles"></a>Статьи, близкие к новым или измененным статьям

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Предметные области, *содержащие* новые или недавно обновленные статьи

- [Новые + обновленные (11+6): &nbsp; &nbsp;**Углубленная аналитика для SQL** (документация)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (18+0): &nbsp;&nbsp;**Analysis Services для SQL** (документация)](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (218+14):  **Подключение к SQL** (документация)](../connect/new-updated-connect.md)
- [Новые + обновленные (14+0): &nbsp; &nbsp;**Ядро СУБД для SQL** (документация)](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (3+2): &nbsp; &nbsp;**Integration Services для SQL** (документация)](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (3+3): &nbsp; &nbsp;**Linux для SQL** (документация)](../linux/new-updated-linux.md)
- [Новые + обновленные (7+10): &nbsp; &nbsp;**Реляционные базы данных для SQL** (документация)](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (0+2): &nbsp; **&nbsp;Reporting Services для SQL** (документация)](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (1+3): &nbsp; &nbsp;**SQL Operations Studio** (документация)](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новые + обновленные(2+3): &nbsp; &nbsp;**Microsoft SQL Server** (документация)](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (1+1): &nbsp; &nbsp;**SQL Server Data Tools (SSDT)** (документация)](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (5+2): &nbsp; &nbsp;**SQL Server Management Studio (SSMS)** (документация)](../ssms/new-updated-ssms.md)
- [Новые + обновленные (0+2): &nbsp; &nbsp;**Transact-SQL** (документация)](../t-sql/new-updated-t-sql.md)
- [Новые + обновленные (1+1): &nbsp;**&nbsp;Инструменты для SQL** (документация)](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Предметные области, *не* содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0):  **Analytics Platform System для SQL** (документация)](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../samples/new-updated-samples.md)
- [Новые + обновленные (0+0): **помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)

