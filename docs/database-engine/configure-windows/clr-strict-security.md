---
title: Строгая безопасность среды CLR | Документы Майкрософт
description: Настройка строгой безопасности среды CLR в SQL Server
ms.custom: ''
ms.date: 06/20/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- clr strict security
- clr_strict_security_TSQL
- clr strict security
- strict_security_TSQL
helpviewer_keywords:
- assemblies [CLR integration], strick security
- clr strict security option
ms.assetid: ''
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: 8b255f03070bffb289184a1dbf6ec9fdedbbec4a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66799517"
---
# <a name="clr-strict-security"></a>Строгая безопасность среды CLR   
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Управляет интерпретацией разрешения `SAFE`, `EXTERNAL ACCESS`, `UNSAFE` в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].   

|Значение |Описание | 
|----- |----- | 
|0 |Disabled: обеспечивает обратную совместимость. Использование значение `Disabled` не рекомендуется. | 
|1 |Enabled: заставляет [!INCLUDE[ssde-md](../../includes/ssde-md.md)] игнорировать сведения `PERMISSION_SET` о сборках и всегда интерпретировать их как `UNSAFE`.  Значение [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] по умолчанию — `Enabled`. | 

> [!WARNING]
>  Среда CLR использует управление доступом для кода (CAS) в .NET Framework, которое больше не поддерживается в качестве границы безопасности. Сборки среды CLR, созданные с помощью `PERMISSION_SET = SAFE`, могут получать доступ к внешним системным ресурсам, вызывать неуправляемый код и получать права системного администратора. Начиная с [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)], появился параметр `sp_configure`, называемый `clr strict security`, для повышения безопасности сборок среды CLR. `clr strict security` включен по умолчанию и рассматривает сборки `SAFE` и `EXTERNAL_ACCESS`, как если бы они были помечены `UNSAFE`. Параметр `clr strict security` можно отключить для обеспечения обратной совместимости, но это делать не рекомендуется. Корпорация Майкрософт рекомендует подписывать все сборки с помощью сертификата или асимметричного ключа с соответствующим именем входа, которому предоставлено разрешение `UNSAFE ASSEMBLY` в базе данных master. Администраторы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] также могут добавлять сборки в список сборок, которым должно доверять ядро СУБД. Дополнительные сведения см. в разделе [sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md).

## <a name="remarks"></a>Remarks   

Если параметр `PERMISSION_SET` включен, операторы `CREATE ASSEMBLY` и `ALTER ASSEMBLY` игнорируются во время выполнения, а параметры `PERMISSION_SET` сохраняются в метаданных. Игнорирование параметра минимизирует сбои в выполнении имеющихся в коде операторов.

Аргумент `CLR strict security` имеет тип `advanced option`.  

> [!IMPORTANT]
>  После включения строгой безопасности сборки без подписи загружаться не будут. Необходимо либо изменить, либо заново создать каждую сборку, чтобы она была подписана сертификатом или асимметричным ключом, имеющим соответствующее имя входа с разрешением `UNSAFE ASSEMBLY` на сервере.

## <a name="permissions"></a>Разрешения 

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
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Параметр конфигурации сервера «clr enabled»](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)
