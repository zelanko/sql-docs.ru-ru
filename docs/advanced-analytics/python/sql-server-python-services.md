---
title: "Службы R SQL Server | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/22/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1dea65-40ea-484a-b767-53680c954934
caps.latest.revision: 38
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 140885b86f0f6fa1a56119246c859f143f596726
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="machine-learning-services-with-python"></a>Машинного обучения служб с Python

Python — это язык, который обеспечивает большую гибкость и управления питанием для разнообразных машинного обучения задачи. Библиотеки с открытым исходным кодом для Python включают несколько платформ для настраиваемых нейронных сетей, а также библиотеки для обработки естественного языка. Теперь этот широко используемый язык поддерживается в SQL Server 2017 г CTP 2.0 и более поздних версий.

Так как Python интегрирован с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компонент database engine можно analytics близко к данным, избежав затрат и рисков, связанных с перемещением данных.  Вы можете развернуть машины обучения решения, основанные на Python с помощью удобных и привычных средств, таких как Visual Studio. Ваши рабочие приложения могут получить прогнозы модели, или визуальных элементов из среды выполнения Python 3.5, просто вызвав T-SQL хранимой процедуры.

Этот выпуск включает дистрибутив Anaconda Python, а также новый [revoscalepy](../python/what-is-revoscalepy.md) библиотеки, чтобы увеличить масштаб и производительность компьютера, решения для обучения.

Можно установить все необходимое для начала работы с Python в программе установки SQL Server 2017 г.:

+ **Службы обучения машины (в базе данных):** установить этот компонент, а также ядро базы данных SQL Server, чтобы обеспечить безопасное выполнение скриптов R на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютера.
  
     При выборе этого компонента, расширения устанавливаются в компоненте database engine, чтобы поддерживать выполнение сценариев Python и создается новая служба, [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], чтобы управлять взаимодействием между средой выполнения Python и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра.

+ **Машины обучения Server (изолированный):** при интеграции SQL Server не требуется, установите этот компонент, чтобы получить поддержку Python в Microsoft R Server. Это дает возможность ввода в эксплуатацию решений Python с помощью **mrsdeploy**.
  
     Не устанавливайте этот компонент на том же компьютере, на котором выполняется служб SQL Server машины обучения.


## <a name="additional-resources"></a>Дополнительные ресурсы

[Настройка Python машинного обучения службы в базе данных](setup-python-machine-learning-services.md)

[Учебники Python](../tutorials/sql-server-python-tutorials.md)

