---
title: "Строгая безопасность среды CLR | Документы Майкрософт"
description: "Настройка строгой безопасности среды CLR в SQL Server"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- clr strict security
- clr_strict_security_TSQL
- clr strict security
- strict_security_TSQL
helpviewer_keywords:
- assemblies [CLR integration], strick security
- clr strict security option
ms.assetid: 
caps.latest.revision: 0
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 54f976fac931d9cdc731f4b3e91c433d66310194
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="clr-strict-security"></a>Строгая безопасность среды CLR   
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Управляет интерпретацией разрешения `SAFE`, `EXTERNAL ACCESS`, `UNSAFE` в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].   

|Значение |Описание | 
|----- |----- | 
|0 |Disabled: обеспечивает обратную совместимость. Использование значение `Disabled` не рекомендуется. | 
|1 |Enabled: заставляет [!INCLUDE[ssde-md](../../includes/ssde-md.md)] игнорировать сведения `PERMISSION_SET` о сборках и всегда интерпретировать их как `UNSAFE`.  Значение [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] по умолчанию — `Enabled`. | 

>  [!WARNING]
>  Среда CLR использует управление доступом для кода (CAS) в .NET Framework, которое больше не поддерживается в качестве границы безопасности. Сборки среды CLR, созданные с помощью `PERMISSION_SET = SAFE`, могут получать доступ к внешним системным ресурсам, вызывать неуправляемый код и получать права системного администратора. Начиная с [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)], появился параметр `sp_configure`, называемый `clr strict security`, для повышения безопасности сборок среды CLR. `clr strict security` включен по умолчанию и рассматривает сборки `SAFE` и `EXTERNAL_ACCESS`, как если бы они были помечены `UNSAFE`. Параметр `clr strict security` можно отключить для обеспечения обратной совместимости, но это делать не рекомендуется. Корпорация Майкрософт рекомендует подписывать все сборки с помощью сертификата или асимметричного ключа с соответствующим именем входа, которому предоставлено разрешение `UNSAFE ASSEMBLY` в базе данных master. Администраторы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] также могут добавлять сборки в список сборок, которым должно доверять ядро СУБД. Дополнительные сведения см. в разделе [sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md).

## <a name="remarks"></a>Замечания   

Если параметр `PERMISSION_SET` включен, операторы `CREATE ASSEMBLY` и `ALTER ASSEMBLY` игнорируются во время выполнения, а параметры `PERMISSION_SET` сохраняются в метаданных. Игнорирование параметра минимизирует сбои в выполнении имеющихся в коде операторов.

Аргумент `CLR strict security` имеет тип `advanced option`.  

>  [!IMPORTANT]  
>  После включения строгой безопасности сборки без подписи загружаться не будут. Необходимо либо изменить, либо заново создать каждую сборку, чтобы она была подписана сертификатом или асимметричным ключом, имеющим соответствующее имя входа с разрешением `UNSAFE ASSEMBLY` на сервере.

## <a name="permissions"></a>Permissions 

### <a name="to-change-this-option"></a>Изменение параметра  
Требует разрешения `sysadmin` или членства в предопределенной роли сервера `CONTROL SERVER`.

### <a name="to-create-an-clr-assembly"></a>Создание сборки среды CLR   
Для создания сборки среды CLR при включении `CLR strict security` требуются следующие разрешения:

- Пользователь должен иметь разрешение `CREATE ASSEMBLY`.  
- Кроме того, должно выполняться одно из следующих условий:  
  - Сборка должна была подписана сертификатом или асимметричным ключом, имеющим соответствующее имя входа с разрешением `UNSAFE ASSEMBLY` на сервере. Рекомендуется использовать подпись сборки.  
  - База данных имеет `TRUSTWORTHY` свойство со значением `ON` и базы данных, принадлежащие имени входа, имеющем разрешение `UNSAFE ASSEMBLY` на сервере. Использовать этот параметр не рекомендуется.  

  
## <a name="see-also"></a>См. также:  
  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Параметр конфигурации сервера «clr enabled»](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)

