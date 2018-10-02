---
title: Параметр конфигурации сервера "clr enabled" | Документы Майкрософт
ms.custom: ''
ms.date: 06/20/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- assemblies [CLR integration], verifying can run
- clr enabled option
ms.assetid: 0722d382-8fd3-4fac-b4a8-cd2b7a7e0293
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8b47bc92f48b4e5360b1b5a93ca094483df32cc8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47832238"
---
# <a name="clr-enabled-server-configuration-option"></a>Параметр конфигурации сервера «clr enabled»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Используйте параметр «clr enabled», чтобы указать, может ли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]выполнять пользовательские сборки. Параметр clr enabled принимает перечисленные ниже значения. 
  
|Значение|Описание|  
|-----------|-----------------|  
|0|Выполнение сборок не разрешается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|1|Выполнение сборок разрешается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
Только в WOW64. Перезагрузите серверы WOW64, чтобы изменения параметров вступили в силу. Для других типов серверов перезагрузка не требуется.  

При выполнении инструкции RECONFIGURE и изменении значения параметра clr enabled с 1 на 0 все домены приложений, содержащие пользовательские сборки, немедленно выгружаются.  
  
>  **При использовании упрощенных пулов выполнение в среде CLR не поддерживается**. Отключите параметр "clr enabled" или "lightweight pooling". Функции, зависящие от среды CLR и неправильно работающие в режиме волокон, включают **иерархический** тип данных, репликацию и управление на основе политик.  

>  [!WARNING]
>  Среда CLR использует управление доступом для кода (CAS) в .NET Framework, которое больше не поддерживается в качестве границы безопасности. Сборки среды CLR, созданные с помощью `PERMISSION_SET = SAFE`, могут получать доступ к внешним системным ресурсам, вызывать неуправляемый код и получать права системного администратора. Начиная с [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)], появился параметр `sp_configure`, называемый `clr strict security`, для повышения безопасности сборок среды CLR. `clr strict security` включен по умолчанию и рассматривает сборки `SAFE` и `EXTERNAL_ACCESS`, как если бы они были помечены `UNSAFE`. Параметр `clr strict security` можно отключить для обеспечения обратной совместимости, но это делать не рекомендуется. Корпорация Майкрософт рекомендует подписывать все сборки с помощью сертификата или асимметричного ключа с соответствующим именем входа, которому предоставлено разрешение `UNSAFE ASSEMBLY` в базе данных master. Администраторы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] также могут добавлять сборки в список сборок, которым должно доверять ядро СУБД. Дополнительные сведения см. в разделе [sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md).
  
## <a name="example"></a>Пример  
 В следующем примере сначала отображается текущая настройка параметра clr enabled, а затем параметр включается с заданием значения 1. Чтобы отключить этот параметр, задайте значение 0.  
  
```sql  
EXEC sp_configure 'clr enabled';  
EXEC sp_configure 'clr enabled' , '1';  
RECONFIGURE;    
```  
  
## <a name="see-also"></a>См. также:  
 [Параметр конфигурации сервера «использование упрощенных пулов»](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Параметр конфигурации сервера «использование упрощенных пулов»](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)  
  
  
