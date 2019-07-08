---
title: Мгновенная инициализация файлов базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- initializing files [SQL Server]
- instant file initialization [SQL Server]
- fast file initialization [SQL Server]
- file initialization [SQL Server]
- IFI [SQL Server]
- database instant file initialization [SQL Server]
ms.assetid: 1ad468f5-4f75-480b-aac6-0b01b048bd67
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 41906481891908c85daf22c223e77826baa27766
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67581990"
---
# <a name="database-file-initialization"></a>Инициализация файлов базы данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Файлы данных и журналов инициализируются, чтобы перезаписать все существующие данные на диске, оставшиеся после удаленных файлов. Файлы данных и журналов сначала инициализируются путем обнуления (заполнения нулями) при выполнении одной из следующих операций:  
  
- Создание базы данных.  
- Добавление файлов данных и журналов к существующей базе данных.  
- Увеличение размера существующего файла (включая операции автоувеличения).  
- Восстановление базы данных или файловой группы.  
  
Вследствие инициализации файлов эти операции занимают больше времени. Однако, если данные записываются в файлы первый раз, операционной системе не требуется заполнять файлы нулями.  
  
## <a name="instant-file-initialization-ifi"></a>Мгновенная инициализация файлов (IFI)  
В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файлы данных могут инициализироваться мгновенно во избежание операций обнуления. Мгновенная инициализация файлов позволяет быстро выполнять упомянутые ранее файловые операции. Мгновенная инициализация файлов освобождает место на диске, не заполняя пространство нулями. Вместо этого содержимое диска перезаписывается, поскольку в файлы записываются новые данные. Файлы журналов не могут быть инициализированы мгновенно.  
  
> [!NOTE]
> Мгновенная инициализация файлов доступна только в [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxppro](../../includes/winxppro-md.md)] , [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] или более поздних версиях.  
> 
> [!IMPORTANT]
> Мгновенная инициализация файлов доступна только для файлов данных. Файлы журналов всегда будут обнуляться при создании или увеличении размера.
  
Мгновенная инициализация файлов доступна, только если стартовой учетной записи службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставлено разрешение *SE_MANAGE_VOLUME_NAME*. Участники группы администраторов Windows обладают этим правом и могут предоставить его другим пользователям, добавив их в политику безопасности **Выполнение задач обслуживания томов** .  
  
> [!IMPORTANT]
> Некоторые условия, например [прозрачное шифрование данных](../../relational-databases/security/encryption/transparent-data-encryption.md), могут не допускать мгновенную инициализацию файлов.  
  
Предоставление учетной записи разрешения `Perform volume maintenance tasks` .  
  
1.  На компьютере, где будет создан файл данных, откройте приложение **Локальная политика безопасности** (`secpol.msc`).  
  
2.  Разверните на левой панели узел **Локальные политики**, а затем щелкните пункт **Назначение прав пользователей**.  
  
3.  На правой панели дважды щелкните **Выполнение задач по обслуживанию томов**.  
  
4.  Выберите пункт **Добавить пользователя или группу** и добавьте учетную запись, от имени которой запущена служба SQL Server.  
  
5.  Нажмите кнопку **Применить**и закройте все диалоговые окна **Локальная политика безопасности** .  

1. Перезапустите службу SQL Server.

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

> [!NOTE]
> Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], это разрешение можно предоставлять учетной записи службы во время установки. При использовании [установки из командной строки](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) добавьте аргумент /SQLSVCINSTANTFILEINIT либо установите флажок *Предоставить право на выполнение задач обслуживания тома службе ядра СУБД SQL Server* в [мастере установки](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).

> [!NOTE]
> Начиная с версий [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] с пакетом обновления 4 (SP4) и [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом обновления 1 (SP1), вплоть до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], вы можете использовать столбец *instant_file_initialization_enabled* в динамическом административном представлении [sys.dm_server_services](../../relational-databases/system-dynamic-management-views/sys-dm-server-services-transact-sql.md) для определения, включена ли мгновенная инициализация файлов.

## <a name="remarks"></a>Remarks
Если учетной записи запуска службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставлено разрешение *SE_MANAGE_VOLUME_NAME*, во время запуска в журнале ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] регистрируется подобное информационное сообщение. 

`Database Instant File Initialization: enabled. For security and performance considerations see the topic 'Database Instant File Initialization' in SQL Server Books Online. This is an informational message only. No user action is required.`

Если учетной записи запуска службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **не предоставлено** разрешение *SE_MANAGE_VOLUME_NAME*, во время запуска в журнале ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] регистрируется подобное информационное сообщение. 

`Database Instant File Initialization: disabled. For security and performance considerations see the topic 'Database Instant File Initialization' in SQL Server Books Online. This is an informational message only. No user action is required.`

**Применимо к:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] с пакетом обновления 4 (SP4), [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] с пакетом обновления 2 (SP2) и версий с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])

## <a name="security-considerations"></a>Соображения безопасности  
При использовании мгновенной инициализации файлов (IFI), так как удаленное содержимое диска перезаписывается только по мере записи в файлы новых данных, пока в помеченную удаленной область файла данных не будут записаны другие данные, неавторизованный субъект может получить доступ к удаленному содержимому. По мере подключения файла базы данных к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] риск раскрытия информации уменьшается благодаря списку управления доступом на уровне пользователей (DACL) в файле. DACL разрешает доступ к файлу только учетной записи службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и локальному администратору. Но при отсоединении файла доступ к нему может получить пользователь или служба, которым не предоставлено разрешение *SE_MANAGE_VOLUME_NAME*. Аналогичная проблема существует при резервном копировании базы данных. Если файл резервной копии не защищен с помощью соответствующего DACL, удаленное содержимое может стать доступным неавторизованному пользователю или службе.  

Следует учитывать и то, что при увеличении файла с помощью IFI администратор SQL Server потенциально может получить доступ к содержимому необработанных страниц и просматривать ранее удаленное содержимое.

Если файлы базы данных размещаются в сети хранения данных, она может всегда представлять новые страницы в виде предварительно инициализированных, что может создавать излишнюю нагрузку, так как операционной системе требуется инициализировать эти страницы повторно.
 
> [!NOTE]
> Если сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлен в защищенной физической среде, выигрыш в производительности от мгновенной инициализации файлов может перевесить риск нарушения безопасности. Именно поэтому мы приводим здесь эту рекомендацию.
  
Если вероятность раскрытия удаленного содержимого является серьезной проблемой, необходимо выполнить одно следующее действие или оба.  
  
- Всегда проверяйте, что все отсоединенные файлы данных и резервные копии имеют ограничивающие DACL.  
- Отключите мгновенную инициализацию файлов для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], отменив разрешение *SE_MANAGE_VOLUME_NAME* стартовой учетной записи службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 

> [!IMPORTANT]
> Отключение мгновенной инициализации файлов приведет к увеличению времени распределения файлов данных.  
  
> [!NOTE]  
> Отключение мгновенной инициализации файлов влияет только на создаваемые или увеличивающиеся в размере файлы после отзыва прав пользователя.  
  
## <a name="see-also"></a>См. также:  
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
  
