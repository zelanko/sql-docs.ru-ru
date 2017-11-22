---
title: "Обратная совместимость в SMO | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2f986436-aaf2-4eaf-9809-df849d97d4fb
caps.latest.revision: "12"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7a2d55e44e12fe3e4d57d2d1e8911899c51d1ce4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="backward-compatibility-in-smo"></a>Обратная совместимость в SMO
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Приложения объектов SMO, написанные с помощью предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно перекомпилировать посредством объектов SMO в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="migrating-smo-applications"></a>Миграция приложений объектов SMO  
 Ссылки на DLL-библиотеки SMO в более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должны быть удалены, а на их место необходимо вставить ссылки на новые DLL-библиотеки SMO, представленные в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Необходимо предоставить ссылки, как минимум, на следующие файлы:  
  
-   Microsoft.SqlServer.ConnectionInfo  
  
-   Microsoft.SqlServer.Smo  
  
-   Microsoft.SqlServer.Management.Sdk.Sfc  
  
 Эти файлы необходимы для классов соединений, служебных классов SMO и классов SFC.  
  
> [!NOTE]  
>  Файл SmoEnum.dll удален. Ссылка на этот файл должна быть удалена из проекта SMO [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Пространства имен также были изменены. Воспользуйтесь следующими:  
  
##### <a name="for-visual-c"></a>Для Visual C#  
  
```  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Common;  
```  
  
##### <a name="for-visual-basic"></a>Для Visual Basic  
  
```  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
```  
  
 Если в коде используется функциональность URN типа **Server.GetSqlSmoObject(Urn)**, необходимо установить связь с пространством имен Microsoft.SqlServer.Management.Sdk.Sfc.  
  
 Если данный код использует передачу объектов непосредственно, необходимо установить связь с пространством имен Microsoft.SqlServer.Management.SmoExtended.  
  
 В случае выполнения миграции кода, может понадобиться изменение кода. Это происходит потому, что некоторые функции [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] устарели. Дополнительные сведения об устаревших средствах см. в разделе [устаревшие функции компонента Database Engine в SQL Server 2016](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md) в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] электронной документации.  
  
  
