---
title: "Архитектура | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1328a346dd9852cba349e38204b49faf32573611
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="architecture-overview-for-machine-learning-services-with-python"></a>Общие сведения об архитектуре служб обучения машины с Python

Здесь представлен обзор интеграции Python с SQL Server, включая модель безопасности, компоненты database engine, который поддерживает выполнение внешних скриптов и новые компоненты, которые позволяет взаимодействовать Python с SQL Server. Дополнительные сведения см. в связанных разделах.

> [!IMPORTANT]
> Поддержка Python — доступны, начиная с SQL Server 2017 г CTP 2.0. Эта функция предварительной версии подлежит изменению.

## <a name="python-interoperability"></a>Взаимодействие с Python

Обучение машины службы (в базе данных) для SQL Server устанавливает дистрибутив Anaconda Python и среда выполнения Python 3.5 и интерпретатора. Это обеспечивает совместимость с рядом завершения с помощью стандартных решений Python. Python выполняется в отдельном процессе с SQL Server, чтобы гарантировать, что операций базы данных не скомпрометирован.

Дополнительные сведения о взаимодействии SQL Server с Python см. в разделе [взаимодействие Python](../../advanced-analytics/python/python-interoperability.md)

## <a name="components-that-support-python-integration"></a>Компоненты, которые поддерживают интеграцию с Python

Инфраструктура расширяемости, появившийся в SQL Server 2016, теперь поддерживает выполнение сценария Python, путем добавления новых компонентов языка. Эти компоненты повысить скорость обмена данными и сжатие, обеспечивая при этом безопасный, высокопроизводительный платформу для выполнения внешних скриптов.

Подробное описание компонентов, которые поддерживают Python, такие как [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] и PythonLauncher, в разделе [новые компоненты](../../advanced-analytics/python/new-components-in-sql-server-to-support-python-integration.md).

## <a name="security"></a>безопасность

Python задачи выполняются вне процесса SQL Server, для обеспечения безопасности и управляемости больше.

Все задачи, защищены с помощью объекты заданий Windows или безопасности SQL Server. Данные хранятся в пределах границ соответствия, обеспечение безопасности SQL Server на уровне экземпляра, базы данных и таблицы. Администратор базы данных можно управлять, кто имеет возможность выполнения заданий Python, отслеживать использование сценариев Python пользователями и просматривать ресурсы, используемые.

Дополнительные сведения см. в разделе [безопасности для Python](../../advanced-analytics/python/security-overview-sql-server-python-services.md)

## <a name="resource-governance"></a>Управление ресурсами

В SQL Server Enterprise Edition контролировать и отслеживать использование ресурсов операций внешних скриптов, включая сценарий R и сценариев Python можно использовать регулятор ресурсов.

Дополнительные сведения см. в разделе [управление ресурсами для R](../../advanced-analytics/r/resource-governance-for-r-services.md).

## <a name="next-steps"></a>Следующие шаги

[Выполнения Python, с помощью T-SQL](../tutorials/run-python-using-t-sql.md)
