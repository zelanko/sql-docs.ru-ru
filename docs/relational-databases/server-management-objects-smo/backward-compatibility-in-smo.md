---
title: Обратная совместимость в SMO | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 2f986436-aaf2-4eaf-9809-df849d97d4fb
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 013dfc93c5e6acfa22d4283cbb0460a1c8f97c23
ms.sourcegitcommit: f3f83ef95399d1570851cd1360dc2f072736bef6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2019
ms.locfileid: "70148770"
---
# <a name="backward-compatibility-in-smo"></a>Обратная совместимость в SMO
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Приложения объектов SMO, написанные с помощью предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , можно повторно компилировать с помощью объекта SMO в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="migrating-smo-applications"></a>Миграция приложений объектов SMO  
 Ссылки на DLL-библиотеки SMO в более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должны быть удалены, а на их место необходимо вставить ссылки на новые DLL-библиотеки SMO, представленные в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
 Необходимо предоставить ссылки, как минимум, на следующие файлы:  
  
-   Microsoft.SqlServer.ConnectionInfo  
  
-   Microsoft.SqlServer.Smo  
  
-   Microsoft.SqlServer.Management.Sdk.Sfc  
  
 Эти файлы необходимы для классов соединений, служебных классов SMO и классов SFC.  
  
> [!NOTE]  
>  Файл SmoEnum.dll удален. Ссылка на этот файл должна быть удалена из проекта SMO [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
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
  
 Если в коде используется функциональность URN типа **Server.GetSqlSmoObject(Urn)** , необходимо установить связь с пространством имен Microsoft.SqlServer.Management.Sdk.Sfc.  
  
 Если данный код использует передачу объектов непосредственно, необходимо установить связь с пространством имен Microsoft.SqlServer.Management.SmoExtended.  
  
 В случае выполнения миграции кода, может понадобиться изменение кода. Это происходит потому, что некоторые функции [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]устарели. Дополнительные сведения об устаревших функциях см. в разделе [устаревшие ядро СУБД функции в SQL Server 2016](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md) электронной документации по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
  
