---
title: Установка SMO | Документы Microsoft
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.prod_service: database-engine
ms.component: smo
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- installing SMO
- SMO [SQL Server], installing
- SQL Server Management Objects, installing
ms.assetid: 140e9971-4940-4866-89b9-5cec938e2a16
caps.latest.revision: 46
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1acdf8bd989730949aa67a2e9a769d1a0dcb1485
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
#<a name="installing-smo"></a>Установка SMO

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Эта страница содержит сведения по установке объектов SMO для использования приложениями и требования к системе для использования объектов SMO.

## <a name="smo-nuget-package"></a>Пакет NuGet SMO

Начиная с версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SMO 2017 г распространяется в виде [Microsoft.SqlServer.SqlManagementObjects](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) пакет NuGet, чтобы разрешить пользователям разработки приложений с помощью объектов SMO.

Это замена для SharedManagementObjects.msi, который ранее был выпущен как часть пакета дополнительных компонентов SQL для каждого выпуска SQL Server. Приложения, использующие SMO должны быть обновлены для использования пакета NuGet вместо и будет отвечать за обеспечение двоичные файлы устанавливаются вместе с разрабатываемого приложения.

>>[!Important]
>>Как упоминалось в [файлы и номера версий](files-and-version-numbers.md) страницы, не следует устанавливать сборки объектов SMO в глобальном кэше СБОРОК. Это может вызвать проблемы с другими приложениями, которые также используют эти версии SMO (такие как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio).

##<a name="installing-the-package"></a>Установка пакета

В разделе [быстрый запуск NuGet - использование пакета](https://docs.microsoft.com/en-us/nuget/quickstart/use-a-package) инструкции и примеры для установки и использования пакета NuGet. 
  
## <a name="system-requirements"></a>Требования к системе
  
 SMO требует [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.0 для запуска, поэтому все использующие его приложения необходимо убедиться, что клиентские компьютеры этой версии или более позднее.
  
