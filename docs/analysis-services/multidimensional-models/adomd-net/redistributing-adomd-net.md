---
title: "Распространение ADOMD.NET | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- ADOMD.NET, redistributing
- redistributing ADOMD.NET
ms.assetid: f8db3c99-0243-4b92-b486-0d8786c264f4
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6587a23e479522453feb01bf7190cebc9fb505df
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="redistributing-adomdnet"></a>Распространение ADOMD.NET
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]При создании приложений, в которых используется компонент ADOMD.NET, соответствующую версию этого компонента необходимо распространять вместе с приложением. Для распространения компонента ADOMD.NET следует включить программу установки ADOMD.NET в программу установки приложения.  
  
 Программу установки компонента ADOMD.NET, а также последнюю версию компонента ADOMD.NET можно найти в центре загрузки Майкрософт в составе пакета дополнительных компонентов SQL Server.  
  
 Программа установки компонента ADOMD.NET устанавливает файлы ADOMD.NET в \< *системный диск*>: \Program Files\Microsoft.NET\ADOMD.NET\\*номер версии*.  
  
 После включения программы установки компонента ADOMD.NET в программе установки приложения необходимо предусмотреть запуск программы установки ADOMD.NET и установку этого компонента. Кроме того, в зависимости от конкретной среды, возможно, потребуется сделать связанные сборки доверенными для SQL Server.  
  
 Дополнительные сведения см. в следующих разделах:  
  
 [Пакет дополнительных компонентов для Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=389949)  
  
 [Microsoft Connect: Зависимости объектов ADOMD.NET](http://go.microsoft.com/fwlink/?LinkId=389950)  
  
## <a name="see-also"></a>См. также:  
 [Программирование клиента ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)   
 [Программирование сервера ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  
