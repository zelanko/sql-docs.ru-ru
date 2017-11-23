---
title: "Реализация сборок | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: assemblies [CLR integration], implementing
ms.assetid: c228d7bf-a906-4f37-a057-5d464d962ff8
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dadb7fe14a03bfd94350ea280cca94494e3c163b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="assemblies---implementing"></a>Сборки - реализация
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Этот раздел содержит сведения о следующих областях, чтобы помочь в реализации и работе со сборками в базе данных:  
  
-   Создание сборок.  
  
-   Изменение сборок.  
  
-   Удаление, отключение и включение сборок.  
  
-   Управление версиями сборок.  
  
## <a name="creating-assemblies"></a>Создание сборок.  
 Сборки создаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY или в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] с использованием редактора сборок. При развертывании проекта SQL Server в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] регистрирует сборку в базе данных, указанной для проекта. Дополнительные сведения см. в статье [Deploying CLR Database Objects](../../relational-databases/clr-integration/deploying-clr-database-objects.md).  
  
 **Чтобы создать сборку с помощью Transact-SQL**  
  
-   [CREATE ASSEMBLY (Transact-SQL)](../../t-sql/statements/create-assembly-transact-sql.md)  
  
 **Чтобы создать сборку с помощью SQL Server Management Studio**  
  
-   [Свойства сборки &#40; Страница "Общие" &#41;](../../relational-databases/clr-integration/assemblies-properties.md)  
  
## <a name="modifying-assemblies"></a>Изменение сборок  
 Сборки изменяются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY или в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] с использованием редактора сборок. Можно изменить сборку, когда надо сделать следующее.  
  
-   Изменить реализацию сборки путем передачи более новой версии бинарных файлов сборки. Дополнительные сведения см. в разделе [управление версиями сборок](#_managing) далее в этом разделе.  
  
-   Изменить набор разрешений сборки. Дополнительные сведения см. в разделе [проектирование сборки](../../relational-databases/clr-integration/assemblies-designing.md).  
  
-   Изменить видимость сборки. Видимые сборки доступны для ссылок на них в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Невидимые сборки недоступны, даже если они были переданы в базу данных. По умолчанию, сборки, переданные в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], видимы.  
  
-   Добавить или удалить отладку или исходный файл, связанный со сборкой.  
  
 **Чтобы изменить сборку с помощью Transact-SQL**  
  
-   [ALTER ASSEMBLY (Transact-SQL)](../../t-sql/statements/alter-assembly-transact-sql.md)  
  
 **Чтобы изменить сборку с помощью SQL Server Management Studio**  
  
-   [Свойства сборки &#40; Страница "Общие" &#41;](../../relational-databases/clr-integration/assemblies-properties.md)  
  
## <a name="dropping-disabling-and-enabling-assemblies"></a>Удаление, отключение и включение сборок  
 Сборки удаляются с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP ASSEMBLY или среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Чтобы удалить сборку с помощью Transact-SQL**  
  
-   [DROP ASSEMBLY (Transact-SQL)](../../t-sql/statements/drop-assembly-transact-sql.md)  
  
 **Чтобы удалить сборку с помощью SQL Server Management Studio**  
  
-   [Удаление объектов](http://msdn.microsoft.com/library/49541441-179c-40d3-ba0c-01bcae545984)  
  
 По умолчанию, все сборки, созданные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], отключены от выполнения. Можно использовать **включена среда clr** параметр **sp_configure** системной хранимой процедуры для отключения или включения выполнения всех сборок, загруженных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Отключение выполнения сборки не допускает выполнения функций среды CLR, хранимых процедур, триггеров, статистических выражений и определяемых пользователем типов, а также останавливает все эти объекты, выполняющиеся в настоящее время. Отключение выполнения сборки не отключает способность создавать, изменять или удалять сборки. Дополнительные сведения см. в разделе [параметра конфигурации сервера «clr enabled»](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md).  
  
 **Чтобы отключить и включить выполнение сборки**  
  
-   [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
##  <a name="_managing"></a>Управление версиями сборок  
 Когда сборка передана в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сборка сохраняется и управляется в пределах системных каталогов базы данных. Любые изменения, внесенные в определение сборки в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] должны распространяться на сборку, которая хранится в каталоге базы данных.  
  
 Если нужно изменить сборку, следует выполнить инструкцию ALTER ASSEMBLY, чтобы обновить сборку в базе данных. Это обновит сборку до последней копии модулей [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], поддерживая ее реализацию.  
  
 Предложение WITH UNCHECKED DATA инструкции ALTER ASSEMBLY сообщает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обновить даже те сборки, от которых зависят материализованные данные в базе данных. В частности, надо указать WITH UNCHECKED DATA, если присутствует любое из следующего.  
  
-   Материализованные вычисляемые столбцы, которые ссылаются на методы в сборке либо непосредственно, либо косвенно — через функции и методы [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Столбцы определяемого пользователем типа CLR, зависящих от сборки и типов, реализующих **UserDefined** (отличных**собственного**) формат сериализации.  
  
> [!CAUTION]  
>  Если не указан параметр WITH UNCHECKED DATA, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] старается избежать выполнения ALTER ASSEMBLY, если сборка новой версии изменяет существующие данные в таблицах, индексах и т. д. Однако при обновлении сборки в среде CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не обеспечивает согласованности вычисляемых столбцов, индексов, индексированных представлений или выражений с базовыми процедурами или типами. Следует проявлять осторожность при исполнении ALTER ASSEMBLY, чтобы избежать несоответствия результата выражения и его значения, хранящегося в сборке.  
  
 Только члены **db_owner** и **db_ddlowner** предопределенной роли базы данных могут выполнять запуск ALTER ASSEMBLY с помощью предложения WITH UNCHECKED DATA.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отправляет сообщение в журнал событий приложений Windows о том, что сборка была изменена непроверенными данными в таблицах. Затем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отмечает любые таблицы, содержащие данные, зависящие от сборки, как таблицы с непроверенными данными. **Has_unchecked_assembly_data** столбец **sys.tables** представление каталога содержит значение 1 для таблиц, содержащих непроверенные данные и 0 для таблиц без непроверенных данных.  
  
 Чтобы проверить целостность непроверенных данных, запустите DBCC CHECKDB с EXTENDED_LOGICAL_CHECKS для каждой таблицы с непроверенными данными. Если инструкция DBCC CHECKDB с EXTENDED_LOGICAL_CHECKS завершается ошибкой, необходимо удалить строки таблицы, которые являются недопустимыми или изменить код сборки для решения проблем и затем выполнить дополнительные инструкции ALTER ASSEMBLY.  
  
 Инструкция ALTER ASSEMBLY изменяет версию сборки. Язык и региональные параметры и маркер открытого ключа сборки не изменяются. SQL Server не допускает регистрации различных версий сборок с одинаковыми именами, культурой и открытый ключ.  
  
### <a name="interactions-with-computer-wide-policy-for-version-binding"></a>Взаимодействие с политикой уровня компьютера для привязки версии  
 Если обращение к сохраненным в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сборкам перенаправляются к определенным версиям, с помощью политики издателя или политики администратора уровня компьютера необходимо сделать любое из следующего.  
  
-   Убедиться, что новая версия, к которой происходит переадресация, находится в базе данных.  
  
-   Изменить любые инструкции по отношению к файлам внешней политики компьютера или политики издателя, чтобы убедиться, что они ссылаются на определенную версию, которая находится в базе данных.  
  
 Иначе попытка загрузить новую версию сборки в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потерпит неудачу.  
  
 **Чтобы обновить версию сборки**  
  
-   [ALTER ASSEMBLY (Transact-SQL)](../../t-sql/statements/alter-assembly-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [Сборки &#40; компонент Database Engine &#41;](../../relational-databases/clr-integration/assemblies-database-engine.md)   
 [Получение сведений о сборках](../../relational-databases/clr-integration/assemblies-getting-information.md)  
  
  
