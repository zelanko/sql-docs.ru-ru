---
title: Устранение неполадок исправности ресурсов SQL Server (служебная программа SQL Server) | Документация Майкрософт
description: Сведения об устранении проблем с работоспособностью ресурсов, которые идентифицирует точка управления служебной программой SQL Server, например чрезмерная загрузка ЦП, недостаток места в файле или выделенного дискового пространства.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 614f07b5-f221-4013-9f8d-22964cf42270
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c6c6d499d485941d490848b68b5c8142edd0cb4b
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2020
ms.locfileid: "91810698"
---
# <a name="troubleshoot-sql-server-resource-health-sql-server-utility"></a>Устранение неполадок исправности ресурсов SQL Server (служебная программа SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Устранение неполадок исправности ресурсов, обнаруженных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP, может потребовать устранения перегрузки ЦП на компьютере или экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также устранения перегрузки ЦП для приложения уровня данных. Также могут потребовать устранения такие проблемы, как использование файлами баз данных слишком большой части файлового пространства или выделение слишком большого места на диске в томе хранилища.  
  
 Обратите внимание, что если база данных находится в аварийном режиме, состояние работоспособности покажет чрезмерное использование пространства для файла журнала.  
  
 Дополнительные сведения об ошибках при сборе данных, вызывающих отображение серых значков в представлении списка управляемых экземпляров в UCP, см. в разделе [Устранение неполадок служебной программы SQL Server](/previous-versions/sql/sql-server-2016/ee210592(v=sql.130)). Дополнительные сведения о начале работы со служебной программой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Функции и задачи служебной программы SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  
  
 Дополнительные сведения об устранении конкретных проблем, связанных с исправностью ресурсов, обнаруженных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP, см. в следующих разделах.  
  
-   [Как определить версию и выпуск установленного SQL Server](https://go.microsoft.com/fwlink/?LinkID=178504)  
  
-   [Устранение связанных с производительностью неполадок в SQL Server 2008](/previous-versions/sql/sql-server-2008/dd672789(v=sql.100))  
  
