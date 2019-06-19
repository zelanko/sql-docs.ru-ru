---
title: Сохранение пакета программным образом | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- programmatically saving a package
- saving a package programmatically
ms.assetid: 4204f817-d5df-475a-9338-d7f01305d566
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 07c926a292c657eecceb13ca1cdc1d3f8dcc5a71
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65729263"
---
# <a name="saving-a-package-programmatically"></a>Сохранение пакета программным образом

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
  
  
