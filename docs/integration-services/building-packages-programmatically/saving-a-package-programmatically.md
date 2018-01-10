---
title: "Сохранение пакета программным образом | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: building-packages-programmatically
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- programmatically saving a package
- saving a package programmatically
ms.assetid: 4204f817-d5df-475a-9338-d7f01305d566
caps.latest.revision: "17"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 138fbb64c49e26b3f223ffe3253914002c58931a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="saving-a-package-programmatically"></a>Сохранение пакета программным образом
  После программного построения нового или изменения существующего пакета обычно необходимо сохранить изменения.  
  
 Все методы, используемые в данном разделе для сохранения пакетов, требуют наличия ссылки на сборку **Microsoft.SqlServer.ManagedDTS** . После добавления ссылки в новый проект импортируйте пространство имен <xref:Microsoft.SqlServer.Dts.Runtime> с помощью инструкции **using** или **Imports**.  
  
## <a name="saving-a-package-programmatically"></a>Сохранение пакета программным образом  
 Для программного сохранения пакета вызовите один из следующих методов класса <xref:Microsoft.SqlServer.Dts.Runtime.Application> служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:  
  
|Место хранения|Вызываемый метод|  
|----------------------|--------------------|  
|Файл|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToXml%2A>|  
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServer%2A><br /><br /> или диспетчер конфигурации служб<br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServerAs%2A>|  
  
> [!IMPORTANT]  
>  Методы класса <xref:Microsoft.SqlServer.Dts.Runtime.Application> для работы с хранилищем пакетов служб SSIS поддерживают только «.» и имя сервера для локального сервера. Использование имен «(local)» и «localhost» невозможно.  
  
## <a name="see-also"></a>См. также:  
 [Сохранение пакетов](../../integration-services/save-packages.md)  
  
  
