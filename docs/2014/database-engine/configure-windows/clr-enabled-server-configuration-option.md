---
title: Параметр конфигурации сервера "clr enabled" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- assemblies [CLR integration], verifying can run
- clr enabled option
ms.assetid: 0722d382-8fd3-4fac-b4a8-cd2b7a7e0293
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a796426f02c2ad9c0878c212c51eb0e90cfce8bf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219384"
---
# <a name="clr-enabled-server-configuration-option"></a>Параметр конфигурации сервера «clr enabled»
  Используйте параметр «clr enabled», чтобы указать, может ли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]выполнять пользовательские сборки. Параметр clr enabled предлагает следующие значения.  
  
|Значение|Описание|  
|-----------|-----------------|  
|0|Выполнение сборок не разрешается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|1|Выполнение сборок разрешается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 Чтобы изменения этого параметра вступили в силу, необходимо перезагрузить серверы WOW64. Для других типов серверов перезагрузка необязательна.  
  
> [!NOTE]  
>  При выполнении инструкции RECONFIGURE и изменении значения параметра «clr enabled» с 1 на 0 все домены приложений, содержащих пользовательские сборки, немедленно выгружаются.  
  
> [!NOTE]  
>  Выполнение в среде CLR не поддерживается при использовании упрощенных пулов. Отключите один из двух параметров: clr enabled или lightweight pooling. Функции, зависящие от среды CLR и должным образом, не работают в режиме волокон, включают `hierarchy` тип данных, репликации и управление на основе политик.  
  
## <a name="example"></a>Пример  
 В следующем примере сначала отображается текущая настройка параметра clr enabled, а затем параметр включается с заданием значения 1. Чтобы отключить этот параметр, задайте значение 0.  
  
```  
EXEC sp_configure 'clr enabled';  
EXEC sp_configure 'clr enabled' , '1';  
RECONFIGURE;  
  
```  
  
## <a name="see-also"></a>См. также  
 [Параметр конфигурации сервера «использование упрощенных пулов»](lightweight-pooling-server-configuration-option.md)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Параметр конфигурации сервера «использование упрощенных пулов»](lightweight-pooling-server-configuration-option.md)  
  
  
