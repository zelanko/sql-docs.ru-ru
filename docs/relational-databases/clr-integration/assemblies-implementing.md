---
title: Внедрение ассамблей Документы Майкрософт
description: Узнайте, как работать с сборками, размещенными на сервере S'L, втомя в том числе о том, как создавать/модифицировать сборки, отключать или включать/отключать сборки, а также управлять версиями.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], implementing
ms.assetid: c228d7bf-a906-4f37-a057-5d464d962ff8
author: rothja
ms.author: jroth
ms.openlocfilehash: 807ed6a6f0d59444cd38f7fdf902a7c3fc1b47d8
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488053"
---
# <a name="assemblies---implementing"></a>Реализация сборок
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Эта тема предоставляет сведения о следующих областях, чтобы помочь в реализации и работе со сборками в базе данных.  
  
-   Создание сборок.  
  
-   Изменение сборок.  
  
-   Удаление, отключение и включение сборок.  
  
-   Управление версиями сборок.  
  
## <a name="creating-assemblies"></a>Создание сборок.  
 Сборки создаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY или в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] с использованием редактора сборок. Кроме того, развертывание проекта сервера [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] S'L в регистрирует сборку в базе данных, которая была указана для проекта. Дополнительные сведения см. в статье [Deploying CLR Database Objects](../../relational-databases/clr-integration/deploying-clr-database-objects.md).  
  
 **Создание сборки с помощью Transact-SQL**  
  
-   [CREATE ASSEMBLY (Transact-SQL)](../../t-sql/statements/create-assembly-transact-sql.md)  
  
 **Создание сборки с помощью среды SQL Server Management Studio**  
  
-   [Собрание Свойства &#40;Генеральный&#41;Страницы](../../relational-databases/clr-integration/assemblies-properties.md)  
  
## <a name="modifying-assemblies"></a>Изменение сборок  
 Сборки изменяются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY или в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] с использованием редактора сборок. Можно изменить сборку, когда надо сделать следующее.  
  
-   Изменить реализацию сборки путем передачи более новой версии бинарных файлов сборки. Для получения дополнительной информации, [см.](#_managing)  
  
-   Изменить набор разрешений сборки. Дополнительные сведения см. в разделе [Разработка сборок](../../relational-databases/clr-integration/assemblies-designing.md).  
  
-   Изменить видимость сборки. Видимые сборки доступны для ссылок на них в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Невидимые сборки недоступны, даже если они были переданы в базу данных. По умолчанию, сборки, переданные в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], видимы.  
  
-   Добавить или удалить отладку или исходный файл, связанный со сборкой.  
  
 **Чтобы изменить сборку с помощью Transact-SQL**  
  
-   [ALTER ASSEMBLY (Transact-SQL)](../../t-sql/statements/alter-assembly-transact-sql.md)  
  
 **Чтобы изменить сборку с помощью среды SQL Server Management Studio**  
  
-   [Собрание Свойства &#40;Генеральный&#41;Страницы](../../relational-databases/clr-integration/assemblies-properties.md)  
  
## <a name="dropping-disabling-and-enabling-assemblies"></a>Удаление, отключение и включение сборок  
 Сборки удаляются с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP ASSEMBLY или среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Чтобы удалить сборку с помощью Transact-SQL**  
  
-   [DROP ASSEMBLY (Transact-SQL)](../../t-sql/statements/drop-assembly-transact-sql.md)  
  
 **Чтобы удалить сборку с помощью среды SQL Server Management Studio**  
  
-   [Удаление объектов](../../ssms/object/delete-objects.md)  
  
 По умолчанию, все сборки, созданные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], отключены от выполнения. Вы можете использовать опцию **включенного clr** процедуры sp_configure **системы,** чтобы отключить или включить выполнение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]всех сборок, загруженных в . Отключение выполнения сборки не допускает выполнения функций среды CLR, хранимых процедур, триггеров, статистических выражений и определяемых пользователем типов, а также останавливает все эти объекты, выполняющиеся в настоящее время. Отключение выполнения сборки не отключает способность создавать, изменять или удалять сборки. Для получения дополнительной [clr enabled Server Configuration Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)информации см.  
  
 **Чтобы отключить и включить выполнение сборки**  
  
-   [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
##  <a name="managing-assembly-versions"></a><a name="_managing"></a>Версия для сборки  
 Когда сборка передана в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сборка сохраняется и управляется в пределах системных каталогов базы данных. Любые изменения, внесенные в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] определение сборки в собрании, должны распространяться на сборку, которая хранится в каталоге базы данных.  
  
 Если нужно изменить сборку, следует выполнить инструкцию ALTER ASSEMBLY, чтобы обновить сборку в базе данных. Это обновит сборку до последней копии модулей [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], поддерживая ее реализацию.  
  
 Предложение WITH UNCHECKED DATA инструкции ALTER ASSEMBLY сообщает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обновить даже те сборки, от которых зависят материализованные данные в базе данных. В частности, надо указать WITH UNCHECKED DATA, если присутствует любое из следующего.  
  
-   Материализованные вычисляемые столбцы, которые ссылаются на методы в сборке либо непосредственно, либо косвенно — через функции и методы [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   зависящие от сборки столбцы определяемого пользователем типа данных CLR и типа, реализующего сериализацию формата **UserDefined** (не **собственного**);  
  
> [!CAUTION]  
>  Если не указан параметр WITH UNCHECKED DATA, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] старается избежать выполнения ALTER ASSEMBLY, если сборка новой версии изменяет существующие данные в таблицах, индексах и т. д. Однако при обновлении сборки в среде CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не обеспечивает согласованности вычисляемых столбцов, индексов, индексированных представлений или выражений с базовыми процедурами или типами. Следует проявлять осторожность при исполнении ALTER ASSEMBLY, чтобы избежать несоответствия результата выражения и его значения, хранящегося в сборке.  
  
 Только члены **db_owner** и **db_ddlowner** фиксированной роли базы данных могут выполнять выполнение ALTER ASSEMBLY с помощью положения С UNCHECKED DATA.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отправляет сообщение в журнал событий приложений Windows о том, что сборка была изменена непроверенными данными в таблицах. Затем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отмечает любые таблицы, содержащие данные, зависящие от сборки, как таблицы с непроверенными данными. **В has_unchecked_assembly_data** столбца представления каталога **sys.tables** содержит значение 1 для таблиц, содержащих непроверенные данные, и 0 для таблиц без неконтролируемых данных.  
  
 Чтобы разрешить целостность непроверенных данных, запустите DBCC CHECKDB с EXTENDED_LOGICAL_CHECKS с каждой таблицей, которая имеет непроверенные данные. Если DBCC CHECKDB с EXTENDED_LOGICAL_CHECKS не удается, необходимо либо удалить строки таблицы, которые не являются действительными, либо изменить код сборки для устранения проблем, а затем выдать дополнительные операторы ALTER ASSEMBLY.  
  
 Инструкция ALTER ASSEMBLY изменяет версию сборки. Культура и общественный ключ маркер сборки остаются теми же. Сервер SL не позволяет регистрировать различные версии сборки с одинаковым названием, культурой и общедоступным ключом.  
  
### <a name="interactions-with-computer-wide-policy-for-version-binding"></a>Взаимодействие с политикой уровня компьютера для привязки версии  
 Если обращение к сохраненным в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сборкам перенаправляются к определенным версиям, с помощью политики издателя или политики администратора уровня компьютера необходимо сделать любое из следующего.  
  
-   Убедиться, что новая версия, к которой происходит переадресация, находится в базе данных.  
  
-   Изменить любые инструкции по отношению к файлам внешней политики компьютера или политики издателя, чтобы убедиться, что они ссылаются на определенную версию, которая находится в базе данных.  
  
 Иначе попытка загрузить новую версию сборки в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потерпит неудачу.  
  
 **Чтобы обновить версию сборки**  
  
-   [ALTER ASSEMBLY (Transact-SQL)](../../t-sql/statements/alter-assembly-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [Сборки &#40;&#41;двигателя базы данных](../../relational-databases/clr-integration/assemblies-database-engine.md)   
 [Получение сведений о сборках](../../relational-databases/clr-integration/assemblies-getting-information.md)  
  
  
