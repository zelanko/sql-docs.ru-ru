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
ms.openlocfilehash: 2785054fa9cc445b6ff03c46f7f145b4f422cb60
ms.sourcegitcommit: f3f83ef95399d1570851cd1360dc2f072736bef6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2019
ms.locfileid: "70148630"
---
# <a name="installing-smo"></a>Установка SMO

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

На этой странице содержатся сведения об установке объектов SMO для использования приложениями и требованиях к системе для использования объектов SMO.

## <a name="smo-nuget-package"></a>Пакет NuGet SMO

Начиная с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2017 SMO распространяется как пакет NuGet [Microsoft. SqlServer. склманажементобжектс](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) , чтобы позволить пользователям разрабатывать приложения с помощью объектов SMO.

Это замена для SharedManagementObjects. msi, которая ранее была выпущена как часть пакета дополнительных компонентов SQL для каждого выпуска SQL Server. Приложения, использующие объекты SMO, должны быть обновлены для использования пакета NuGet. он будет отвечать за обеспечение установки двоичных файлов вместе с разрабатываемым приложением.

>>[!Important]
>>Как упоминалось на странице [файлы и номера версий](files-and-version-numbers.md) , не следует устанавливать сборки SMO в глобальный кэш сборок. Это может вызвать проблемы с другими приложениями, которые также используют эти версии объектов SMO (например, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio).

## <a name="installing-the-package"></a>Установка пакета

Инструкции и примеры установки и использования пакета NuGet см. [в разделе NuGet быстрое начало — использование пакета](https://docs.microsoft.com/nuget/quickstart/use-a-package) . 
  
## <a name="system-requirements"></a>Требования к системе
  
 Для работы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] объектов SMO требуется 4,0, поэтому все приложения, использующие ее, должны гарантировать, что на клиентских компьютерах установлена эта версия или более поздняя. Для некоторых собственных двоичных файлов, установленных с помощью библиотек SMO, также требуется установка среды выполнения VC 2013. Эта среда выполнения не включена в пакет. Вы можете скачать распространяемый файл, соответствующий целевой архитектуре, из https://www.microsoft.com/download/details.aspx?id=40784
  
