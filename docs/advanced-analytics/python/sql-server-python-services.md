---
title: "Машинного обучения служб с помощью Python | Документы Microsoft"
ms.date: 03/16/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: 47762e531cc3b0f78a17b19da80ad3ea2249a086
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2018
---
# <a name="machine-learning-services-with-python"></a>Машинного обучения служб с Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Python — это язык, который обеспечивает большую гибкость и управления питанием для разнообразных машинного обучения задачи. Библиотеки с открытым исходным кодом для Python включают несколько платформ для настраиваемых нейронных сетей, а также библиотеки для обработки естественного языка. Теперь этот широко применяемый язык поддерживается в SQL Server 2017 г машинного обучения.

Так как Python интегрирован с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компонент database engine можно analytics близко к данным, избежав затрат и рисков, связанных с перемещением данных.  Вы можете развернуть машины обучения решения, основанные на Python с помощью удобных и привычных средств, таких как Visual Studio. Ваши рабочие приложения могут получить прогнозы модели, или визуальных элементов из среды выполнения Python 3.5, просто вызвав T-SQL хранимой процедуры.

Этот выпуск включает дистрибутив Anaconda Python, а также [revoscalepy](../python/what-is-revoscalepy.md) библиотеки, чтобы увеличить масштаб и производительность компьютера, решения для обучения.

Можно установить все необходимое для начала работы с Python в программе установки SQL Server 2017 г.:

+ [**Компьютер службы обучения (в базе данных)**](../install/sql-machine-learning-services-windows-install.md): Установите этот компонент, а также ядро базы данных SQL Server, чтобы обеспечить безопасное выполнение сценариев Python в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютера.
  
     При выборе этого компонента, расширения устанавливаются в компоненте database engine, чтобы поддерживать выполнение сценариев Python и создается новая служба, [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], чтобы управлять взаимодействием между средой выполнения Python и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра.

+ [**Машинного обучения Server (изолированный)**](../install/sql-machine-learning-standalone-windows-install.md): Если интеграции SQL Server не требуется, установите этот компонент для получения поддержки Python и R для распределенных машинного обучения.

## <a name="see-also"></a>См. также:

+ [SQL Server машинного обучения и служб R (в базе данных)](../r/sql-server-r-services.md)
+ [SQL Server машинного обучения и R Server (изолированный)](../r/r-server-standalone.md)
+ [Архитектура Python](architecture-overview-sql-server-python.md)
+ [Учебники Python](../tutorials/sql-server-python-tutorials.md)
