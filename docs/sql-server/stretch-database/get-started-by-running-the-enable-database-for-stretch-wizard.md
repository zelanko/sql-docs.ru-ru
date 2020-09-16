---
description: Запуск мастера включения растяжения для базы данных
title: Запуск мастера включения растяжения для базы данных
ms.date: 08/05/2016
ms.service: sql-server-stretch-database
ms.reviewer: ''
ms.topic: quickstart
f1_keywords:
- sql13.swb.stretchwizard.f1
- sql13.swb.stretchwizard.createdatabasecredentials.f1
- sql13.swb.stretchwizard.selectdatabasetables.f1
- sql13.swb.stretchwizard.validatesqlserver.f1
- sql13.swb.stretchwizard.selectazuredeployment.f1
- sql13.swb.stretchwizard.configureazuredeployment.f1
- sql13.swb.stretchwizard.Summary.f1
- sql13.swb.stretchwizard.Results.f1
- sql13.swb.stretchwizard.introduction.f1
helpviewer_keywords:
- Stretch Database, wizard
- Enable Database for Stretch Wizard
ms.assetid: 855dd9fc-f80c-4dbc-bf46-55a9736bfe15
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: 6b06f82e5c51aa1c3843abec0daa7d3bebabe40a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454368"
---
# <a name="get-started-by-running-the-enable-database-for-stretch-wizard"></a>Запуск мастера включения растяжения для базы данных
[!INCLUDE [sqlserver2016-windows-only](../../includes/applies-to-version/sqlserver2016-windows-only.md)]


 Для настройки базы данных для Stretch Database запустите мастер "Включение Stretch Database для базы данных".  Эта статья содержит сведения о параметрах, используемых в этом мастере.  
  
 Дополнительные сведения о Stretch Database см. [здесь](../../sql-server/stretch-database/stretch-database.md). 
 
 > [!NOTE] 
 > В случае последующего отключения Stretch Database для таблицы или базы данных помните, что такое отключение не приводит к удалению дистанционного объекта. Если вы хотите удалить удаленную таблицу или базу данных, это нужно сделать с помощью портала управления Azure. Пока удаленные объекты не будут удалены вручную, их хранение будет сопровождаться затратами в Azure. 
  
## <a name="launch-the-wizard"></a>Запуск мастера  
  
1.  В SQL Server Management Studio в обозревателе объектов выберите базу данных, для которой нужно включить растяжение.  
  
2.  Щелкните правой кнопкой мыши и выберите **Задачи**, затем **Растяжение**и щелкните **Включить** для запуска мастера.  
  
##  <a name="introduction"></a><a name="Intro"></a> Введение  
 Изучите информацию о назначении мастера и предварительные требования.  
 
 Важные предварительные требования перечислены ниже.
 -   Для внесения изменений в базу данных необходимо быть администратором.
 -   Требуется подписка на Microsoft Azure.
 -   SQL Server должен иметь возможность подключения к удаленному серверу Azure.
  
 ![Вводная страница мастера Stretch Database](../../sql-server/stretch-database/media/stretch-wizard-1.png "Вводная страница мастера Stretch Database")  
  
##  <a name="select-tables"></a><a name="Tables"></a> Выбор таблиц  
 Выберите таблицы, которые необходимо включить для растяжения.  
 
Таблицы с большим количеством строк отображаются в начале отсортированного списка. Прежде чем вывести список таблиц, мастер анализирует данные таблиц, чтобы обнаружить типы данных, которые в настоящее время не поддерживаются в Stretch Database. 
  
 ![Страница выбора таблиц в мастере Stretch Database](../../sql-server/stretch-database/media/stretch-wizard-2.png "Страница выбора таблиц в мастере Stretch Database")  
  
|Столбец|Описание|  
|------------|-----------------|  
|(нет имени)|Установите флажок в этом столбце для включения растяжения для выбранной таблицы.|  
|**Имя**|Указывает имя таблицы в базе данных.|  
|(нет имени)|Символ в этом столбце может означать предупреждение, не позволяющее включить поддержку Stretch для выбранной таблицы. Кроме того, он может указывать на проблему блокировки, не позволяющую включить выбранную таблицу для Stretch, например связанную с тем, что в таблице используется неподдерживаемый тип данных. Наведите указатель на символ, чтобы увидеть всплывающую подсказку с дополнительной информацией. Дополнительные сведения см. в статье об [ограничениях для Stretch Database](../../sql-server/stretch-database/limitations-for-stretch-database.md).|  
|**Растянута**|Указывает, что в таблице уже включена поддержка Stretch.|  
|**анализа**|Можно перенести всю таблицу (**Вся таблица**) или указать фильтр для одного из столбцов в этой таблице. Если вы хотите отобрать строки для переноса, использую другую функцию фильтра, после выхода из мастера выполните инструкцию ALTER TABLE, чтобы указать функцию фильтра. Дополнительные сведения о функции фильтров см. в статье [Выбор строк для миграции с использованием функции фильтров](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md). Дополнительные сведения о способах применения функции см. в статье [Настройка Stretch Database для таблицы](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md) или [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md).|  
|**Строки**|Указывает количество строк в таблице.|  
|**Размер (КБ)**|Указывает размер элемента в килобайтах.|  
  
## <a name="optionally-provide-a-row-filter"></a>При необходимости укажите фильтр строк  
 Если вы хотите отобрать строки для переноса, используя другую функцию фильтра, выполните указанные ниже действия на странице **Выбор таблиц** .  
  
1.  В списке **Выберите таблицы, которые требуется растянуть** выберите пункт **Вся таблица** в строке соответствующей таблицы. Откроется диалоговое окно **Выбор строк для растяжения** .  
  
     ![Определение предиката фильтра на основе даты](../../sql-server/stretch-database/media/stretch-wizard-2a.png "Определение предиката фильтра на основе даты")  
  
2.  В диалоговом окне **Выбор строк для растяжения** выберите пункт **Выбрать строки**.  
  
3.  В поле **Имя**укажите имя функции фильтра.  
  
4.  В предложении **Где** выберите столбец из таблицы, укажите оператор и введите значение.  
  
5.  Нажмите кнопку **Проверить** , чтобы протестировать функцию. Если функция возвращает результаты из таблицы (т. е. имеются соответствующие условию строки для переноса), проверка завершается с результатом **Успешно**.  

> [!NOTE] 
> Текстовое поле, в котором отображается запрос фильтра, доступно только для чтения. Изменить запрос в текстовом поле нельзя.
  
6.  Нажмите кнопку "Готово", чтобы вернуться на страницу **Выбор таблиц** .  

Функция фильтра создается в SQL Server только после завершения работы мастера. А пока это не произошло, вы можете вернуться на страницу **Выбор таблиц** и изменить или переименовать функцию фильтра.

![Страница выбора таблицы после определения предиката фильтра](../../sql-server/stretch-database/media/stretch-wizard-2b.png "Страница выбора таблицы после определения предиката фильтра")

Если вы хотите использовать другой тип функции фильтров, чтобы выбрать строки для переноса, выполните одно из следующих действий.  
  
-   Закройте мастер и выполните инструкцию ALTER TABLE, чтобы включить растяжение для таблицы и указать функцию фильтров. Дополнительные сведения см. в статье [Включение Stretch Database для таблицы](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md).  
  
-   Выполните инструкцию ALTER TABLE, чтобы указать функцию фильтров после выхода из мастера. Необходимые пошаговые инструкции см. в статье [Добавление функции фильтров после запуска мастера](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md#addafterwiz).  
  
##  <a name="configure-azure"></a><a name="Configure"></a> Настройка Azure  
  
1.  Войдите в Microsoft Azure с учетной записью Майкрософт.  
  
     ![Вход в Azure — мастер Stretch Database](../../sql-server/stretch-database/media/stretch-wizard-3.png "Вход в Azure — мастер Stretch Database")  
  
2.  Выберите имеющуюся подписку Azure, которая будет использоваться для Stretch Database. 

> [!NOTE] 
> Чтобы включить растяжение в базе данных, требуются права администратора используемой подписки. Мастер базы данных Stretch отобразит только подписки, в которых пользователь имеет права администратора.
  
3.  Выберите регион Azure, который будете использовать для Stretch Database.
    -   Новый сервер будет создан в этом регионе.  
    -   Если в выбранном регионе имеется несколько серверов, мастер выдаст их список при выборе пункта **Существующий сервер**.
  
     Чтобы свести к минимуму задержки, выбирайте тот регион Azure, в котором находится SQL Server. Дополнительные сведения о регионах см. в статье [Регионы Azure](https://azure.microsoft.com/regions/).  
  
4.  Укажите, следует ли использовать существующий сервер Azure или создать новый.  
  
     Если Active Directory на сервере SQL Server состоит в федерации с Azure Active Directory, вы можете выбрать для взаимодействия SQL Server с удаленным сервером Azure федеративную учетную запись службы. Дополнительные сведения о требованиях для этого параметра см. в статье [ALTER DATABASE SET Options (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
    -   **Создание сервера**  
  
        1.  Создайте имя для входа и пароль администратора сервера.  
  
        2.  Вы также можете использовать федеративную учетную запись службы для взаимодействия SQL Server с удаленным сервером Azure.  
  
         ![Создание нового сервера Azure — мастер Stretch Database](../../relational-databases/tables/media/stretch-wizard-4.png "Создание нового сервера Azure — мастер Stretch Database")  
  
    -   **Существующий сервер**  
  
        1.  Выберите существующий сервер Azure.  
  
        2.  Выберите метод проверки подлинности.  
  
            -   Если выбран параметр **Проверка подлинности SQL Server**, введите имя и пароль администратора.  
  
            -   Выберите метод **Встроенная проверка подлинности Active Directory** , чтобы использовать федеративную учетную запись службы для взаимодействия SQL Server с удаленным сервером Azure. Если выбранный сервер не интегрирован с Azure Active Directory, этот параметр не отображается.
  
         ![Выбор существующего сервера Azure — мастер Stretch Database](../../sql-server/stretch-database/media/stretch-wizard-5.png "Выбор существующего сервера Azure — мастер Stretch Database")  
  
##  <a name="secure-credentials"></a><a name="Credentials"></a> Защищенные учетные данные  
 У вас должен быть главный ключ базы данных для защиты учетных данных, используемых при подключении к удаленной базе данных, использующей Stretch Database.  
  
 Если главный ключ базы данных уже существует, введите соответствующий пароль.  
  
 ![Страница "Учетные данные безопасности" мастера Stretch Database](../../sql-server/stretch-database/media/stretch-wizard-6b.PNG "Страница "Учетные данные безопасности" мастера Stretch Database")  
  
 Если главного ключа для базы данных нет, введите надежный пароль, чтобы создать такой ключ.  
  
 ![Страница "Учетные данные безопасности" мастера Stretch Database](../../relational-databases/tables/media/stretch-wizard-6.png "Страница "Учетные данные безопасности" мастера Stretch Database")  
  
 Дополнительные сведения о главном ключе базы данных см. в разделах [CREATE MASTER KEY (Transact-SQL)](../../t-sql/statements/create-master-key-transact-sql.md) и [Создание главного ключа базы данных](../../relational-databases/security/encryption/create-a-database-master-key.md). Дополнительные сведения о создаваемых мастером учетных данных см. в разделе [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).  
  
##  <a name="select-ip-address"></a><a name="Network"></a> Выбор IP-адреса  
 Используя диапазон IP-адресов подсети (рекомендуется) или общедоступный IP-адрес сервера SQL Server, создайте в Azure правило брандмауэра, которое позволит SQL Server обмениваться данными с удаленным сервером Azure.  
  
 Сервер Azure будет использовать IP-адрес или адреса, которые вы укажете на этой странице, для разрешения пропуска через брандмауэр Azure входящих данных, запросов и операций управления, инициированных SQL Server. Мастер не вносит изменения в параметры брандмауэра на сервере SQL Server.  
  
 ![Страница "Выбор IP-адреса" мастера Stretch Database](../../relational-databases/tables/media/stretch-wizard-7.png "Страница "Выбор IP-адреса" мастера Stretch Database")  
  
##  <a name="summary"></a><a name="Summary"></a> Сводка  
 Просмотрите значения, которые вы ввели или выбрали в мастере, а также оценку предполагаемых затрат на использование Azure. Нажмите кнопку **Готово** , чтобы включить растягивание.  
  
 ![Страница сводки в мастере Stretch Database](../../sql-server/stretch-database/media/stretch-wizard-8.png "Страница сводки в мастере Stretch Database")  
  
##  <a name="results"></a><a name="Results"></a> Результаты  
 Просмотрите результаты.  
  
 Инструкции по отслеживанию состояния переноса данных см. в статье [Мониторинг переноса данных и устранение неполадок при этой операции (Stretch Database)](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md).  
  
 ![Страница результатов в мастере Stretch Database](../../sql-server/stretch-database/media/stretch-wizard-9.PNG "Страница результатов в мастере Stretch Database")  
  
##  <a name="troubleshooting-the-wizard"></a><a name="KnownIssues"></a> Устранение неполадок в работе мастера  
 **Сбой в работе мастера подготовки Stretch Database.**  
 Если служба Stretch Database еще не включена на уровне сервера системным администратором и вы запускаете мастер, то его работа завершится неудачно. Попросите системного администратора активировать использование базы данных Stretch на экземпляре локального сервера, а затем повторно запустите мастер. Дополнительные сведения см. в разделе [Обязательное требование: разрешение на включение базы данных Stretch на сервере](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md#EnableTSQLServer).  
  
## <a name="next-steps"></a>Дальнейшие шаги  
 Включите Stretch Database для других таблиц. Мониторинг миграции данных и управление базами данных и таблицами с поддержкой Stretch.  
  
-   [Включение Stretch Database для таблицы](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md), чтобы активировать дополнительные таблицы.  
  
-   Инструкции по отслеживанию статуса переноса данных см. в разделе [Мониторинг и устранение неполадок переноса данных (Stretch Database)](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md).  
  
-   [Приостановка и возобновление переноса данных (Stretch Database)](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md)  
  
-   [Управление службой Stretch Database и устранение неполадок, связанных с ее использованием](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md)  
  
-   [Резервное копирование баз данных с поддержкой Stretch](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md)  
  
-   [Восстановление баз данных с поддержкой Stretch](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)  
  
## <a name="see-also"></a>См. также:  
 [Включение Stretch Database для базы данных](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [Настройка базы данных Stretch для таблицы](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md)  
  
  
