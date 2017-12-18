---
title: "Устранение неполадок исправности ресурсов SQL Server (служебная программа SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: maintenance-plans
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 614f07b5-f221-4013-9f8d-22964cf42270
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eb7cb98417cf8eaf78647f4a52fd984be6c338d3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="troubleshoot-sql-server-resource-health-sql-server-utility"></a>Устранение неполадок исправности ресурсов SQL Server (служебная программа SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Устранение неполадок с работоспособностью ресурсов, обнаруженных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP, может потребовать устранения перегрузки ЦП на компьютере или экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также устранения перегрузки ЦП для приложения уровня данных. Также могут потребовать устранения такие проблемы, как использование файлами баз данных слишком большой части файлового пространства или выделение слишком большого места на диске в томе хранилища.  
  
 Обратите внимание, что если база данных находится в аварийном режиме, состояние работоспособности покажет чрезмерное использование пространства для файла журнала.  
  
 Дополнительные сведения об ошибках при сборе данных, вызывающих отображение серых значков в представлении списка управляемых экземпляров в UCP, см. в разделе [Устранение неполадок служебной программы SQL Server](http://msdn.microsoft.com/library/f5f47c2a-38ea-40f8-9767-9bc138d14453). Дополнительные сведения о начале работы со служебной программой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Функции и задачи служебной программы SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  
  
 Дополнительные сведения об устранении конкретных проблем, связанных с исправностью ресурсов, обнаруженных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP, см. в следующих разделах.  
  
-   [Как определить версию и выпуск установленного SQL Server](http://go.microsoft.com/fwlink/?LinkID=178504)  
  
-   [Устранение связанных с производительностью неполадок в SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=151354)  
  
  
