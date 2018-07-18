---
title: Изучение служб с помощью Python машины SQL Server | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b8ef234b0e8c09e3d4be9488b7ac628c225e67f6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31201996"
---
# <a name="sql-server-machine-learning-services-with-python"></a>Изучение служб с помощью Python машины SQL Server
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
