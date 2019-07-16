---
title: Установка SMO | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.reviewer: ''
ms.prod_service: database-engine
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- installing SMO
- SMO [SQL Server], installing
- SQL Server Management Objects, installing
ms.assetid: 140e9971-4940-4866-89b9-5cec938e2a16
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f57fc3ea1a677a2655f5358a1d5c4b27045ea6ab
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68098022"
---
# <a name="installing-smo"></a>Установка SMO

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Эта страница содержит сведения о том, как установить SMO для использования приложениями и требования к системе для использования SMO.

## <a name="smo-nuget-package"></a>Пакет NuGet SMO

Начиная с версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2017 SMO распространяется в виде [Microsoft.SqlServer.SqlManagementObjects](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) пакет NuGet, чтобы разрешить пользователям разрабатывать приложения с использованием объектов SMO.

Это замена для SharedManagementObjects.msi, которая ранее была выпущена как часть пакета дополнительных компонентов SQL для каждого выпуска SQL Server. Приложения, использующие SMO необходимо обновить, чтобы вместо этого используйте пакет NuGet и будет отвечать за соблюдение двоичные файлы устанавливаются вместе с при разработке приложения.

>>[!Important]
>>Как отмечалось на [файлы и номера версий](files-and-version-numbers.md) странице сборки объектов SMO не следует устанавливать в глобальный кэш СБОРОК. Таким образом привести к проблемам с другими приложениями, которые также используют эти версии SMO (такие как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio).

## <a name="installing-the-package"></a>Установка пакета

См. в разделе [быстрого запуска NuGet: использование пакета](https://docs.microsoft.com/nuget/quickstart/use-a-package) инструкции и примеры, установке и использованию пакета NuGet. 
  
## <a name="system-requirements"></a>Требования к системе
  
 Объекты SMO требуются [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.0, чтобы запустить, чтобы все использующие его приложения необходимо убедиться, что клиентские компьютеры этой версии или более поздней. Некоторые собственные двоичные файлы, установленные с библиотеками NetFx SMO также требуется среда выполнения VC 2013 должны быть установлены; среды выполнения не включается в пакет. Вы можете скачать распространяемый пакет, соответствующий целевой архитектуре из https://www.microsoft.com/download/details.aspx?id=40784
  
