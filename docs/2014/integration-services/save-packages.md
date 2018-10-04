---
title: Сохранение пакетов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, saving
- packages [Integration Services], saving
- saving packages
- SSIS packages, saving
- SQL Server Integration Services packages, saving
ms.assetid: 17c1de2c-637f-45c2-a148-79294bae0af4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f8f7b354b70f5e936a7d2953fbbcbbfbd7695114
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48193434"
---
# <a name="save-packages"></a>Сохранение пакетов
  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] пакеты создаются с помощью конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] и сохраняются в файловой системе как XML-файлы (DTSX-файлы). Копии XML-файла пакета можно также сохранять в базе данных msdb в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или в хранилище пакетов. Хранилище пакетов представляет собой папки в определенном месте файловой системы, управляемые службами [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 При сохранении пакета в файловой системе можно в дальнейшем использовать службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , чтобы выполнить импорт пакета в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или в хранилище пакетов. Дополнительные сведения см. в разделе [Импорт и экспорт пакетов (службы SSIS)](../../2014/integration-services/import-and-export-packages-ssis-service.md).  
  
 Можно также использовать программу командной строки **dtutil** для копирования пакета между файловой системой и базой данных msdb. Дополнительные сведения см. в статье [dtutil Utility](dtutil-utility.md).  
  
### <a name="to-save-a-package"></a>Сохранение пакета  
  
-   [Сохранение пакета в файловой системе](../../2014/integration-services/save-a-package-to-the-file-system.md)  
  
-   [Сохранение одной копии пакета](../../2014/integration-services/save-a-copy-of-a-package.md)  
  
  
