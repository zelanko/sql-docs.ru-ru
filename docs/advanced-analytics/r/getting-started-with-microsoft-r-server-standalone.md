---
title: "Приступая к работе с изолированным сервером Microsoft R Server | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: r-server
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52347d0d-ce60-4bb8-98d2-6163e87716b0
caps.latest.revision: 21
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fc7874c6900474c7c2f3d927183616b2f5e69699
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="getting-started-with-microsoft-r-server-standalone"></a>Приступая к работе с изолированным сервером Microsoft R Server
  Изолированный сервер Microsoft R Server позволяет использовать на предприятии популярный язык R с открытым кодом, чтобы внедрять высокопроизводительные аналитические решения и обеспечить интеграцию с другими бизнес-приложениями.  

  
## <a name="install-microsoft-r-server"></a>Установка Microsoft R Server 

Установка R Microsoft Server зависит от того, нужно ли использовать в приложениях данные SQL Server. Если да, тогда следует выполнить установку с помощью программы установки SQL Server. Если данные SQL Server не будут использоваться или не требуется выполнять код R в базе данных, можно использовать программу установки SQL Server или новый автономный установщик.
 
 
+ Установите изолированный сервер Microsoft R Server с помощью программы установки SQL Server. Будет создан отдельный экземпляр двоичных файлов R для R Server, который получит лицензию политики поддержки SQL Server Enterprise Edition. Дополнительные сведения см. в статье [Создание изолированного сервера R Server](../../advanced-analytics/r-services/create-a-standalone-r-server.md).  

+ Используйте новый автономный установщик Windows для создания нового экземпляра Microsoft R Server, который использует политику современного жизненного цикла поддержки программного обеспечения Майкрософт. Дополнительные сведения см. в статье [Install R Server 9.0.1 for Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows) (Установка R Server 9.0.1 для Windows).

+ Если у вас есть экземпляр R Server (изолированный) или служб R, который требуется обновить, необходимо скачать и запустить установщик Windows. Дополнительные сведения см. в статье [Install R Server 9.0.1 for Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows) (Установка R Server 9.0.1 для Windows).
  
## <a name="install-additional-r-tools"></a>Установка дополнительных средств R  

 Мы рекомендуем использовать бесплатную версию [Microsoft R Client](http://aka.ms/rclient/download) (скачать).  

 Также можно использовать предпочтительную среду разработки R, чтобы разрабатывать решения для служб R SQL Server или Microsoft R Server. Дополнительные сведения см. в статье [Установка или настройка средств R](../../advanced-analytics/r-services/setup-or-configure-r-tools.md). 
 

### <a name="location-of-r-server-binaries"></a>Расположение двоичных файлов R Server

В зависимости от метода, используемого для установки Microsoft R Server, расположение по умолчанию может отличаться. Прежде чем использовать предпочитаемую среду разработки, проверьте, установлены ли библиотеки R:

+ Microsoft R Server, установленный с помощью нового установщика Windows.

  `C:\Program Files\Microsoft\R Server\R_SERVER`

+ R Server (изолированный), установленный с помощью программы установки SQL Server.

  `C:\Program Files\Microsoft SQL Server\130\R_SERVER`

+ Службы R (в базе данных)

  `C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES`
      
## <a name="start-using-r-on-microsoft-r-server"></a>Начало работы с R на сервере Microsoft R Server  

 После настройки компонентов сервера и интегрированной среды разработки R для использования двоичных файлов R Server можно приступать к разработке решения с помощью новых интерфейсов API, таких как пакет RevoScaleR, MicrosoftML и olapR.
    
Чтобы начать работу с R Server, ознакомьтесь с руководством в библиотеке MSDN [Get started with Microsoft R](https://msdn.microsoft.com/microsoft-r/microsoft-r-get-started-node) (Приступая к работе с Microsoft R Server).   
  
-   [ScaleR.](https://msdn.microsoft.com/microsoft-r/scaler-getting-started) Просмотрите эту коллекцию распространяемых аналитических функций, которые обеспечивают высокую производительность и масштабирование решений R. Она содержит параллелизуемые версии многих популярных пакетов моделирования для R, например кластеризацию методом К-средних, деревья и леса принятия решений, а также средства для работы с данными. Дополнительные сведения см. в статье [Explore R and ScaleR in 25 functions](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started-tutorial) (Обзор R и ScaleR в 25 функциях).  
    
- [MicrosoftML.](https://msdn.microsoft.com/library/mt790482.aspx) Пакет MicrosoftML — это набор новых быстрых и масштабируемых алгоритмов машинного обучения и преобразований, разрабатываемых в Майкрософт. Дополнительные сведения см. в статье [MicrosoftML: State-of-the-Art Machine Learning R Algorithms from Microsoft Corporation](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml) (MicrosoftML. Современные алгоритмы машинного обучения от корпорации Майкрософт).
  


  
## <a name="see-also"></a>См. также:  
 [Начало работы со службами R SQL Server](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)  
  
  

