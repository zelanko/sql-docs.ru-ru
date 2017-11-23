---
title: "Изучение служб машины SQL Server | Документы Microsoft"
ms.date: 11/09/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1dea65-40ea-484a-b767-53680c954934
caps.latest.revision: "38"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Active
ms.openlocfilehash: fb770b52f2cacfc527f6bb89955acfbda243c18a
ms.sourcegitcommit: ec5f7a945b9fff390422d5c4c138ca82194c3a3b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/11/2017
---
# <a name="sql-server-machine-learning-services"></a>Изучение служб машины SQL Server

  Обучение машины служб (ранее служб SQL Server 2016 R) SQL Server 2017 г. предоставляет платформу для разработки и развертывания интеллектуальных приложений, предназначенных для получения новых аналитических данных. Вы можете использовать функциональный и эффективный язык R и множество пакетов от сообщества, чтобы создавать модели и делать прогнозы с использованием данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
  Поскольку машинное обучение интегрирован с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], можно analytics близко к данным, избежав затрат и рисков, связанных с перемещением данных.
  
SQL Server поддерживает язык R с открытым кодом, набор средств и технологий, которые обеспечивают высокую производительность, безопасность, надежность и управляемость. Вы можете развертывать решения R с помощью удобных и привычных средств SQL, а ваши рабочие приложения могут вызывать среду выполнения R и получать прогнозы и визуальные элементы с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]. Можно также получить [Microsoft R](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) библиотек для повышения производительности решений R, включая RevoScaleR, revoscalepy и MicrososftML и масштаб.
  
Через программу установки SQL Server можно установить как серверные, так и клиентские компоненты.
  
## <a name="machine-learning-in-sql-server-2017"></a>Машинного обучения в SQL Server 2017 г.

+ Установка **службы обучения машины (в базе данных)** во время [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] программу установки, чтобы обеспечить безопасное выполнение скриптов R или Python на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютера.
  
    При выборе этого компонента расширения устанавливаются в компоненте database engine для поддержки выполнения кода на языке R или Python. Создается новая служба, [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], для управления обменом данными между внешних сред выполнения и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра.
  
+ Установка **Microsoft машины обучения Server (изолированный)** на отдельном компьютере, если не нужно использовать в качестве контекста вычислений SQL Server. Сервер обучения машины включает компоненты обучения одного компьютера, а также возможность выполнения задач обучения масштабируемая, распределенная машины веб-службы.
  
+    Установка [клиент Microsoft R](https://docs.microsoft.com/r-server/r-client/what-is-microsoft-r-client) на удаленных компьютерах для разработки решений, которые могут быть развернуты в SQL Server или серверу обучения компьютера в Windows, Linux или Hadoop.

## <a name="machine-learning-in-sql-server-2016"></a>Машинного обучения в SQL Server 2016

+ Установка **служб R (в базе данных)** во время установки SQL Server 2016, чтобы обеспечить безопасное выполнение скриптов R на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютера.
  
    При выборе этого компонента вы получаете возможность запустить сценарий R, с помощью SQL Server в контексте или для выполнения сценария R в хранимой процедуре.
  
+   Установка **Microsoft R Server (изолированный)** из программы установки SQL Server 2016, чтобы установить компоненты R на отдельном компьютере, который можно использовать для разработки и развертывания решений R.


## <a name="which-type-of-machine-learning-service-do-i-need"></a>Какой тип службы обучения машины следует предпринять?

+ Если необходимо выполнять код R в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], либо с помощью хранимых процедур или с помощью экземпляра SQL Server в контексте, необходимо установить [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] как описано [здесь](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).

+ Microsoft машины обучения Server (изолированный) является отдельным параметром предназначены для использования [Microsoft R](https://docs.microsoft.com/r-server/r-reference/introducing-r-server-r-package-reference) и [связанные библиотеки Python](../python/what-is-revoscalepy.md) на компьютере Windows, на котором не выполняется SQL Server. Однако его требуется лицензия Enterprise Edition для SQL Server.
    
    Мы рекомендуем установить Microsoft машины обучения Server (изолированный) на ноутбук или другого удаленного компьютера, для использования в разработке и использовать его для создания и тестирования решения обучения машины, которые легко могут быть развернуты на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под управлением службы обучения машины \(в базе данных\) или другой поддерживаемой контекста вычислений.
  
    Можно также использовать **mrsdeploy** пакет, который устанавливается вместе с компьютера сервера обучения для публикации и распространения заданий R и Python веб-службы.

## <a name="additional-resources"></a>Дополнительные ресурсы

+ [Приступая к работе со службами SQL Server R Services](../../advanced-analytics/r/getting-started-with-sql-server-r-services.md)
 
    Описаны типичные сценарии для использования R в SQL Server

+ [Установка служб R SQL Server (в базе данных)](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

    Установить R и связанные базы данных компонентов в рамках программы установки SQL Server
  
+ [Учебники по SQL Server R](../../advanced-analytics/tutorials/sql-server-r-tutorials.md)

    Информация о том, как создавать источники данных SQL Server в коде R и использовать контексты удаленных вычислений. Другие руководства предназначены для разработчиков SQL и демонстрируют, как обучить и развернуть модель R в SQL Server.
