---
title: Распространение ADOMD.NET | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5e3a563c5c51e4852fd477f9acdbf76e31e80dc8
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="redistributing-adomdnet"></a>Распространение ADOMD.NET
  При создании приложений, в которых используется компонент ADOMD.NET, соответствующую версию этого компонента необходимо распространять вместе с приложением. Для распространения компонента ADOMD.NET следует включить программу установки ADOMD.NET в программу установки приложения.  
  
 Программу установки компонента ADOMD.NET, а также последнюю версию компонента ADOMD.NET можно найти в центре загрузки Майкрософт в составе пакета дополнительных компонентов SQL Server.  
  
 Программа установки компонента ADOMD.NET устанавливает файлы ADOMD.NET в \< *системный диск*>: \Program Files\Microsoft.NET\ADOMD.NET\\*номер версии*.  
  
 После включения программы установки компонента ADOMD.NET в программе установки приложения необходимо предусмотреть запуск программы установки ADOMD.NET и установку этого компонента. Кроме того, в зависимости от конкретной среды, возможно, потребуется сделать связанные сборки доверенными для SQL Server.  
  
 Дополнительные сведения см. в следующих разделах:  
  
 [Пакет дополнительных компонентов для Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=389949)  
  
 [Microsoft Connect: Зависимости объектов ADOMD.NET](http://go.microsoft.com/fwlink/?LinkId=389950)  
  
## <a name="see-also"></a>См. также  
 [Программирование клиента ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)   
 [Программирование сервера ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  
