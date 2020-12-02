---
description: Сохранение пакета программным образом
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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4ce0606f8d63015be37b5230a47cb66c82cf1a20
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "88352110"
---
# <a name="saving-a-package-programmatically"></a>Сохранение пакета программным образом

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  После программного построения нового или изменения существующего пакета обычно необходимо сохранить изменения.  
  
 Все методы, используемые в данном разделе для сохранения пакетов, требуют наличия ссылки на сборку **Microsoft.SqlServer.ManagedDTS** . После добавления ссылки в новый проект импортируйте пространство имен <xref:Microsoft.SqlServer.Dts.Runtime> с помощью инструкции **using** или **Imports**.  
  
## <a name="saving-a-package-programmatically"></a>Сохранение пакета программным образом  
 Для программного сохранения пакета вызовите один из следующих методов класса [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <xref:Microsoft.SqlServer.Dts.Runtime.Application>.  
  
|Место хранения|Вызываемый метод|  
|----------------------|--------------------|  
|Файл|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToXml%2A>|  
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServer%2A><br /><br /> или<br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServerAs%2A>|  
  
> [!IMPORTANT]  
>  Методы класса <xref:Microsoft.SqlServer.Dts.Runtime.Application> для работы с хранилищем пакетов служб SSIS поддерживают только «.» и имя сервера для локального сервера. Использование имен «(local)» и «localhost» невозможно.  
  
## <a name="see-also"></a>См. также  
 [Сохранение пакетов](../../integration-services/save-packages.md)  
  
  
