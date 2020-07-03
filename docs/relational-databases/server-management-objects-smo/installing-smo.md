---
title: Установка объектов SMO | Документация Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d6b0608265b44e7ccebd95491554739524bac390
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85894417"
---
# <a name="installing-smo"></a>Установка SMO

[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw.md)]

На этой странице содержатся сведения об установке объектов SMO для использования приложениями и требованиях к системе для использования объектов SMO.

## <a name="smo-nuget-package"></a>Пакет NuGet SMO

Начиная с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2017 SMO распространяется как пакет NuGet [Microsoft. SqlServer. склманажементобжектс](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) , чтобы позволить пользователям разрабатывать приложения с помощью объектов SMO.

Это замена SharedManagementObjects.msi, которая ранее была выпущена как часть пакета дополнительных компонентов SQL для каждого выпуска SQL Server. Приложения, использующие объекты SMO, должны быть обновлены для использования пакета NuGet. он будет отвечать за обеспечение установки двоичных файлов вместе с разрабатываемым приложением.

>>[!Important]
>>Как упоминалось на странице [файлы и номера версий](files-and-version-numbers.md) , не следует устанавливать сборки SMO в глобальный кэш сборок. Это может вызвать проблемы с другими приложениями, которые также используют эти версии объектов SMO (например, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio).

## <a name="installing-the-package"></a>Установка пакета

Инструкции и примеры установки и использования пакета NuGet см. [в разделе NuGet быстрое начало — использование пакета](https://docs.microsoft.com/nuget/quickstart/use-a-package) . 
  
## <a name="system-requirements"></a>Требования к системе
  
 Для работы объектов SMO требуется [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4,0 или .NET Core 2,0, поэтому все приложения, использующие его, должны обеспечивать установку этой версии или более поздней на клиентских компьютерах. Для некоторых собственных двоичных файлов, установленных с помощью библиотек SMO, также требуется установка среды выполнения VC 2013. Эта среда выполнения не включена в пакет. Вы можете скачать распространяемый файл, соответствующий целевой архитектуре, изhttps://www.microsoft.com/download/details.aspx?id=40784
  
