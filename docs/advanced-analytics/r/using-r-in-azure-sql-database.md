---
title: "Использование языка R в базе данных Azure SQL | Документы Microsoft"
ms.custom: 
ms.date: 11/16/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 4562dc3490f4790a31b4b32e06b9e5133a151c67
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="using-r-in-azure-sql-database"></a>Использование языка R в базе данных Azure SQL

В октябре 2017 г. группа разработчиков SQL Server объявила для поддержки выполнения R код в базе данных с помощью хранимых процедур, аналогично R Services в SQL Server 2016.

> [!IMPORTANT]
> Начальной предварительной версии, которая было объявлено предназначена для тестирования и только для просмотра. В настоящее время средство, **отключена** в базе данных SQL Azure для дальнейшей поддержки разработки. 

Чтобы поддерживать актуальность на открытые выпуске расписание и узнать о предстоящих событиях см. в разделе [в блоге SQL Server](https://blogs.technet.microsoft.com/dataplatforminsider/) или [блог Microsoft R Server](https://blogs.msdn.microsoft.com/rserver/).

**Ресурсы Azure**

В то же время рекомендуется использовать один из виртуальных машин 2017 г. SQL Server, доступные в Azure Marketplace. 

+ [Подготовьте виртуальную машину для машинного обучения в Azure](provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)

Также ознакомьтесь с этих виртуальных машинах, которые заранее с различными популярными машинного обучения средства:

+ [Виртуальная машина обработки и анализа данных](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/overview)
+ [Глубокие обучения виртуальной машины](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview), 

