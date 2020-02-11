---
title: Устранение неполадок исправности ресурсов SQL Server (служебная программа SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 614f07b5-f221-4013-9f8d-22964cf42270
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 17eb193f76c0b89cec505133c96d8636b39af55f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62736347"
---
# <a name="troubleshoot-sql-server-resource-health-sql-server-utility"></a>Устранение неполадок исправности ресурсов SQL Server (служебная программа SQL Server)
  Устранение неполадок исправности ресурсов, обнаруженных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP, может потребовать устранения перегрузки ЦП на компьютере или экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также устранения перегрузки ЦП для приложения уровня данных. Также могут потребовать устранения такие проблемы, как использование файлами баз данных слишком большой части файлового пространства или выделение слишком большого места на диске в томе хранилища.  
  
 Обратите внимание, что если база данных находится в аварийном режиме, состояние работоспособности покажет чрезмерное использование пространства для файла журнала.  
  
 Дополнительные сведения об ошибках при сборе данных, вызывающих отображение серых значков в представлении списка управляемых экземпляров в UCP, см. в разделе [Устранение неполадок служебной программы SQL Server](../../database-engine/troubleshoot-the-sql-server-utility.md). Дополнительные сведения о начале работы со служебной программой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Функции и задачи служебной программы SQL Server](sql-server-utility-features-and-tasks.md).  
  
 Дополнительные сведения об устранении конкретных проблем, связанных с исправностью ресурсов, обнаруженных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP, см. в следующих разделах.  
  
-   [Как определить версию и выпуск установленного SQL Server](https://go.microsoft.com/fwlink/?LinkID=178504)  
  
-   [Устранение связанных с производительностью неполадок в SQL Server 2008](https://go.microsoft.com/fwlink/?LinkId=151354)  
  
  
