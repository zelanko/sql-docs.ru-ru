---
title: Просмотр журнала ошибок агента SQL Server (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- viewing SQL Server Agent error logs
- displaying SQL Server Agent error logs
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: de920425-fa44-469f-b83d-49e3f97e97f4
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c5705a237bda9b426b8f39103b9c9fdf19abb00c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65088689"
---
# <a name="view-sql-server-agent-error-log-sql-server-management-studio"></a>View SQL Server Agent Error Log (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе содержатся сведения о просмотре журнала ошибок агента  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
Средство просмотра журнала позволяет просматривать многие журналы различных компонентов. Когда средство просмотра журнала открыто, нужный журнал можно выбрать при помощи панели **Выбор журналов** . В каждом журнале отображаются столбцы, соответствующие типу журнала. Список доступных журналов зависит от того, каким способом было открыто средство просмотра журнала.  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   [Просмотр журнала ошибок агента SQL Server с помощью среды SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
Узел агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отображается в обозревателе объектов только при наличии у пользователя разрешения на использование узла.  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
Для выполнения своих функций агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть настроен на использование учетных данных записи, которая является членом предопределенной роли сервера **sysadmin** в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта учетная запись должна иметь следующие разрешения Windows.  
  
-   Вход в систему в качестве службы (SeServiceLogonRight)  
  
-   Замена токена уровня процесса (SeAssignPrimaryTokenPrivilege)  
  
-   Обход проходной проверки (SeChangeNotifyPrivilege)  
  
-   Назначение квот памяти процессам (SeIncreaseQuotaPrivilege)  
  
Дополнительные сведения о разрешениях Windows, необходимых для учетной записи службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , см. в разделах [Выбор учетной записи для службы агента SQL Server](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) и [Настройка учетных записей служб Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-view-the-includessnoversionincludesssnoversion-mdmd-agent-error-log"></a>Просмотр журнала ошибок агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть сервер, содержащий журнал агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который необходимо просмотреть.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните значок «плюс», чтобы развернуть папку **Журналы ошибок** .  
  
4.  Щелкните правой кнопкой журнал ошибок, который необходимо просмотреть, и выберите **Просмотреть журнал агента**.  
  
    В диалоговом окне **Просмотр файла журнала —**_имя_сервера_ доступны указанные ниже параметры.  
  
    **Загрузить журнал**  
    Открывает диалоговое окно, в котором можно указать загружаемый файл журнала.  
  
    **Экспорт**  
    Открывает диалоговое окно, позволяющее экспортировать данные из сетки **Сведения о файле журнала** в текстовый файл.  
  
    **Обновить**  
    Позволяет обновить представление выбранных журналов. При нажатии кнопки **Обновить** выбранные журналы заново считываются с целевого сервера с применением параметров фильтра.  
  
    **Фильтр**  
    Открывает диалоговое окно, позволяющее указывать параметры фильтрации файла журнала, например **Соединение**и **Дата**или другие **Общие** условия фильтра.  
  
    **Поиск**  
    Позволяет найти определенный текст в файле журнала. Поиск с символами-шаблонами не поддерживается.  
  
    **Остановить**  
    Прекращает загрузку записей файла журнала. Например, можно использовать этот параметр, если загрузка удаленного файла или файла журнала вне сети занимает длительное время, а нужно просмотреть лишь наиболее свежие записи.  
  
    **Сведения о файле журнала**  
    Эта информационная панель содержит сводку данных по фильтрации файла журнала. Если файл не фильтруется, на панели отображается текст **без фильтров**. Если фильтр применяется к журналу, отображается следующий текст **Критерий отбора:** <filter criteria>.  
  
    **Сведения о выбранной строке**  
    Выберите строку для отображения дополнительных сведений о выбранной строке события внизу страницы. Порядок столбцов можно менять, перетаскивая их в нужное место сетки. Размер столбцов можно менять, перетаскивая разделители столбцов в заголовке сетки вправо или влево. Если дважды щелкнуть разделитель столбцов в заголовке сетки, ширина столбца будет автоматически подогнана под его содержимое.  
  
    **Экземпляр**  
    Имя экземпляра, к которому относится происшедшее событие. Отображается как *имя_компьютера*\\*имя_экземпляра*.  
  
    **Дата**  
    Дата события.  
  
    **Source**  
    Исходная функция, создавшая событие, например имя службы (MSSQLSERVER). Отображается не для всех типов журнала.  
  
    **Сообщение**  
    Сообщение, связанное с событием.  
  
    **Log Type**  
    Отображает тип журнала, которому принадлежит событие. Все выбранные журналы отображаются в окне сводки файла журнала.  
  
    **Log Source**  
    Отображает описание исходного журнала, в котором зарегистрировано событие.  
  
5.  После завершения нажмите кнопку **Закрыть**.  
  
