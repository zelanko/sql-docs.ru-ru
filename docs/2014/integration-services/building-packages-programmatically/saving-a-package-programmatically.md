---
title: Сохранение пакета программным образом | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- programmatically saving a package
- saving a package programmatically
ms.assetid: 4204f817-d5df-475a-9338-d7f01305d566
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bba57c5ab732c0b1ed4b7441fae80741701c4f7a
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53371846"
---
# <a name="saving-a-package-programmatically"></a>Сохранение пакета программным образом
  После программного построения нового или изменения существующего пакета обычно необходимо сохранить изменения.  
  
 Все методы, используемые в данном разделе для сохранения пакетов, требуют наличия ссылки на сборку `Microsoft.SqlServer.ManagedDTS`. После добавления ссылки в новый проект импортируйте пространство имен <xref:Microsoft.SqlServer.Dts.Runtime> с помощью инструкции `using` или `Imports`.  
  
## <a name="saving-a-package-programmatically"></a>Сохранение пакета программным образом  
 Для программного сохранения пакета вызовите один из следующих методов класса <xref:Microsoft.SqlServer.Dts.Runtime.Application> служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:  
  
|Место хранения|Вызываемый метод|  
|----------------------|--------------------|  
|Файл|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToXml%2A>|  
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServer%2A><br /><br /> или диспетчер конфигурации служб<br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServerAs%2A>|  
  
> [!IMPORTANT]  
>  Методы класса <xref:Microsoft.SqlServer.Dts.Runtime.Application> для работы с хранилищем пакетов служб SSIS поддерживают только «.» и имя сервера для локального сервера. Использование имен «(local)» и «localhost» невозможно.  
  
![Значок служб Integration Services (маленький)](../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Сохранение пакетов](../save-packages.md)  
  
  
