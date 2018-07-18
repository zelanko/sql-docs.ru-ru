---
title: Установка SMO | Документация Майкрософт
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
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8780920f4b535c77b82f404e84917d4cc97af4e1
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983886"
---
#<a name="installing-smo"></a>Установка SMO

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Эта страница содержит сведения о том, как установить SMO для использования приложениями и требования к системе для использования SMO.

## <a name="smo-nuget-package"></a>Пакет NuGet SMO

Начиная с версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2017 SMO распространяется в виде [Microsoft.SqlServer.SqlManagementObjects](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) пакет NuGet, чтобы разрешить пользователям разрабатывать приложения с использованием объектов SMO.

Это замена для SharedManagementObjects.msi, которая ранее была выпущена как часть пакета дополнительных компонентов SQL для каждого выпуска SQL Server. Приложения, использующие SMO необходимо обновить, чтобы вместо этого используйте пакет NuGet и будет отвечать за соблюдение двоичные файлы устанавливаются вместе с при разработке приложения.

>>[!Important]
>>Как отмечалось на [файлы и номера версий](files-and-version-numbers.md) странице сборки объектов SMO не следует устанавливать в глобальный кэш СБОРОК. Таким образом привести к проблемам с другими приложениями, которые также используют эти версии SMO (такие как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio).

##<a name="installing-the-package"></a>Установка пакета

См. в разделе [быстрого запуска NuGet: использование пакета](https://docs.microsoft.com/nuget/quickstart/use-a-package) инструкции и примеры, установке и использованию пакета NuGet. 
  
## <a name="system-requirements"></a>Требования к системе
  
 Объекты SMO требуются [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.0, чтобы запустить, чтобы все использующие его приложения необходимо убедиться, что клиентские компьютеры этой версии или более поздней.
  
