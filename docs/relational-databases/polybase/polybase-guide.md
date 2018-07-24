---
title: Руководство по PolyBase | Документация Майкрософт
ms.date: 05/30/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: polybase
ms.tgt_pltfrm: ''
ms.topic: get-started-article
f1_keywords:
- PolyBase
- PolyBase, guide
helpviewer_keywords:
- PolyBase
- PolyBase, overview
- Hadoop import ×
- Hadoop export
- Hadoop export, PolyBase overview
- Hadoop import, PolyBase overview
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b94cc6a8a906721c43f1da66867d954fa8f9b50b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37970576"
---
# <a name="polybase-guide"></a>Руководство по PolyBase
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
  PolyBase — это технология, которая обращается к данным за пределами базы данных с помощью языка t-sql.  В SQL Server 2016 она позволяет выполнять запросы к внешним данным в хранилище BLOB-объектов Azure или Hadoop, а также импортировать данные в такое хранилище и экспортировать их из него. Для включения вычислений для Hadoop запросы оптимизируются. В хранилище данных SQL Azure можно импортировать данные из хранилища BLOB-объектов Azure и Azure Data Lake Store и экспортировать данные.
  
  
 Инструкции по работе с PolyBase см. в статье [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md).  
  
 ![Логическая схема использования PolyBase](../../relational-databases/polybase/media/polybase-logical.png "логическая схема использования PolyBase")  
  
## <a name="why-use-polybase"></a>Зачем нужна технология PolyBase  
Чтобы принимать верные решения, необходимо анализировать реляционные данные и другие данные, не структурированные в таблицы, в частности с использованием Hadoop. Для этого требуется способ переноса данных из одного типа хранилища в другой. PolyBase решает эту задачу, работая с данными за пределами SQL Server.  
  
Проще говоря, PolyBase не требует установки дополнительного программного обеспечения в среде Hadoop. При запросе внешних данных используется такой же синтаксис, как при запросе таблицы базы данных. Операции выполняются прозрачно. PolyBase обрабатывает все данные в фоновом режиме, и для успешной работы с этой технологией конечному пользователю знакомство c Hadoop не требуется. 
  
 PolyBase может:  
  
-   **Запрашивать данные, хранящиеся в Hadoop, из SQL Server или PDW.** Пользователи хранят данные в более экономичных распределенных и масштабируемых системах, таких как Hadoop. PolyBase позволяет легко запрашивать данные с помощью T-SQL.  
  
-   **Запрашивать данные, хранящиеся в хранилище BLOB-объектов Azure.** Данные для использования службами Azure удобно хранить в хранилище BLOB-объектов Azure.  PolyBase позволяет легко обращаться к данным с помощью T-SQL.  
  
-   **Импортировать данные из Hadoop, хранилища BLOB-объектов Azure или Azure Data Lake Store.** Используйте скорость технологии Microsoft SQL columnstore и возможности анализа, импортируя данные из Hadoop, хранилища BLOB-объектов Azure или Azure Data Lake Store в реляционные таблицы. Нет необходимости в отдельном средстве ETL или импорта.  

-   **Экспортировать данные в Hadoop, хранилище BLOB-объектов Azure или Azure Data Lake Store.** Архивация данных в Hadoop, хранилище BLOB-объектов Azure или Azure Data Lake Store позволяет создать экономичное хранилище и обеспечить его подключение к сети для удобного доступа к данным.  
  
-   **Интегрироваться со средствами бизнес-аналитики.** Можно использовать PolyBase со средствами бизнес-аналитики и стеком анализа Майкрософт, а также применять любые сторонние средства, совместимые с SQL Server.  
  
## <a name="performance"></a>Производительность  
  
-   **Включение вычислений в Hadoop.** Оптимизатор запросов принимает решение о включении вычислений в Hadoop, если это улучшит производительность запросов.  Для принятия такого решения он использует статистику из внешних таблиц. При включении вычислений создаются задания MapReduce и применяются распределенные вычислительные ресурсы Hadoop.  
  
-   **Масштабирование вычислительных ресурсов.** Для повышения производительности запросов можно использовать [группы горизонтального масштабирования PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md)в SQL Server. Это обеспечивает параллельную передачу данных между экземплярами SQL Server и узлами Hadoop, а также добавляет вычислительные ресурсы для работы с внешними данными.  
  
## <a name="polybase-guide-topics"></a>Статьи руководства по PolyBase  
 Это руководство содержит статьи, которые помогут вам использовать PolyBase более эффективно.  
  
|||  
|-|-|  
|**Раздел**|**Описание**|  
|[Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)|Основные шаги по установке и настройке PolyBase. В статье рассказывается, как создавать внешние объекты, указывающие на данные в Hadoop или хранилище BLOB-объектов Azure, и приводятся примеры запросов.|  
|[Сводка функций PolyBase по версиям](../../relational-databases/polybase/polybase-versioned-feature-summary.md)|В статье описываются компоненты PolyBase, которые поддерживаются в SQL Server, базе данных SQL и хранилище данных SQL.|  
|[группы горизонтального масштабирования PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md)|Параллельное масштабирование между SQL Server и Hadoop с использованием групп горизонтального масштабирования SQL Server.|  
|[Установка PolyBase](../../relational-databases/polybase/polybase-installation.md)|Ссылки и инструкции по установке PolyBase с помощью мастера установки или средства командной строки.|  
|[Конфигурация PolyBase](../../relational-databases/polybase/polybase-configuration.md)|Настройка параметров SQL Server для PolyBase.  Например, настройка включения вычислений и средств безопасности Kerberos.|  
|[Объекты T-SQL PolyBase](../../relational-databases/polybase/polybase-t-sql-objects.md)|Создание объектов T-SQL, которые PolyBase использует для определения внешних данных и доступа к этим данным.|  
|[PolyBase Queries](../../relational-databases/polybase/polybase-queries.md)|Используйте инструкции T-SQL для запроса, импорта или экспорта внешних данных.|  
|[Устранение неполадок c PolyBase](../../relational-databases/polybase/polybase-troubleshooting.md)|Методы управления запросами PolyBase. Используйте динамические административные представления (DMV) для отслеживания запросов PolyBase и узнайте, как считать план запросов PolyBase для поиска узких мест производительности.|  
  
  
