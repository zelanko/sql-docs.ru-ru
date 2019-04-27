---
title: Архитектура системы Change Data Capture Service для Oracle от Attunity | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1db6c737-3c60-4066-a0a3-3611e1c83e4e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 84ac0e6065fa3fb4845e0e3a47ce56816705e80d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62771497"
---
# <a name="change-data-capture-service-for-oracle-by-attunity-system-architecture"></a>Архитектура службы системы отслеживания измененных данных для Oracle компании Attunity
  Служба CDC Service для Oracle отслеживает изменения выбранных таблиц из одной или нескольких исходных баз данных Oracle и записывает сведения о них в базы данных CDC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , расположенные в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . На следующей диаграмме показаны компоненты, составляющие службу CDC Service для Oracle.  
  
 ![Архитектура службы](../media/service-architecture.gif "Архитектура службы")  
  
 На рисунке показано использование четырех платформ. Во многих случаях эти платформы могут дублировать друг друга, однако на диаграмме представлен стандартный вариант использования. Например, часто бывает целесообразно, чтобы Oracle и базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выполнялись на разных компьютерах, а не совместно с платформой службы Oracle CDC Service или платформой, с которой запускается служба CDC Service. На этом рисунке показаны следующие платформы:  
  
-   Служба Oracle CDC Service. Это может быть любой поддерживаемый компьютер Windows, где установлена и запущена служба Oracle CDC. Эта платформа может также представлять собой узел в отказоустойчивом кластере Microsoft (конфигурации высокого уровня доступности описаны далее в этом документе).  
  
-   База данных Oracle. Это может быть любой компьютер, на котором выполняется поддерживаемая версия базы данных Oracle. Сюда входят любые компьютеры, работающие под управлением ОС Windows, Linux или любой другой операционной системы, поддерживаемой версией установленной базы данных Oracle. Следует отметить, что на диаграмме показано несколько таких платформ, поскольку одна служба Oracle CDC Service может отслеживать изменения в нескольких исходных базах данных Oracle.  
  
-   Экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Это может быть любой компьютер, на котором работает целевая база данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (поддерживаемый номер SKU [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]). Служба Oracle CDC Service поддерживает один целевой экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , где хранятся таблицы изменений и конфигурация службы. Платформа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может также представлять собой кластеризованный экземпляр [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] или зеркалированный экземпляр [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с функцией **AlwaysOn** .  
  
-   Конструктор Oracle CDC. Это может быть любой поддерживаемый компьютер с Windows с доступом к базе данных Oracle источника и целевой объект [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных.  
  
 В следующей таблице описаны компоненты, которые выполняются на четырех платформах, указанных выше.  
  
|Компонент/Описание|Компонент включает в себя следующее:|  
|----------------------------|----------------------------|  
|Служба Oracle CDC Service. Это служба Windows, где происходит действие записи данных изменений.|Экземпляр Oracle CDC. Подпроцесс службы Oracle CDC Service, что дескрипторы действия по отслеживанию измененных данных для базы данных Oracle единый источник (имеется один экземпляр Oracle CDC в исходной базе данных Oracle).<br /><br /> Средство чтения журнала Oracle. Читает журналы транзакций Oracle, с помощью клиента Oracle.<br /><br /> Клиент Oracle: Oracle Instant Client используется для связи с Oracle. Это обязательный компонент, который нужно получить у Oracle и установить до установки службы Oracle CDC Service.<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Модуль записи изменений: Записывает зафиксированные изменения, внесенные в отслеживаемые таблицы Oracle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]таблицы изменений. Этот компонент также поддерживает состояние отслеживания в целевой базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Клиент ODBC. Клиент Microsoft Native Client для [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Это обязательный компонент, который нужно получить у Microsoft и установить до установки службы Oracle CDC Service.|  
|Конфигурация службы CDC Oracle. Это оснастка консоли управления, которая создает службу Windows и настраивает ее конфигурацию.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Клиент: Клиент SQL ADO.NET, который поставляется с версии 4 платформы .NET framework.|  
|База данных Oracle. Регистрируются исходной базой данных Oracle из какие изменения выбранных таблиц.|Средство анализа журналов. Компонент Oracle, с помощью которого читаются журналы транзакций Oracle.<br /><br /> Журналы транзакций. Активные и архивированные журналы операций повтора Oracle, используемые Oracle, чтобы убедиться, что базы данных можно выполнить откат транзакций и восстановления после сбоев (в данном случае база данных Oracle необходимо работать в режиме archivelog).|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Экземпляр: Объект [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экземпляра, где размещаются базы данных CDC. Это может быть кластеризованный экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (отказоустойчивый кластер) или зеркальная база данных (с функцией AlwaysOn).|База данных MSXDBCDC. Базы данных где сведения о службе CDC Service, работающей с этим [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] хранятся. Здесь также хранятся сведения об экземплярах Oracle CDC, обрабатываемых каждой службой CDC Service. Эта база данных создается в ходе процесса создания службы CDC Service.<br /><br /> Базы данных CDC. Базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , в которых хранятся изменения одной из баз данных-источников Oracle. В базах данных CDC обеспечена возможность работы CDC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , поэтому у них есть таблицы и функции CDC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , облегчающие прием данных об изменениях, получаемых из Oracle.|  
|Конструктор Oracle CDC. Оснастка консоли управления Майкрософт, которая помогает создавать экземпляры Oracle CDC. Используется для выбора таблиц и столбцов, в которых будут отслеживаться изменения, указания данных подключения к Oracle и управления жизненным циклом экземпляров CDC.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Клиент: Клиент SQL ADO.NET, который поставляется с версии 4 платформы .NET framework.<br /><br /> Клиент Oracle: Oracle Instant Client используется для связи с Oracle. Это обязательный компонент, который нужно получить у Oracle и установить до установки службы Oracle CDC Service.|  
  
 Служба Oracle CDC Service и ее дочерние экземпляры Oracle CDC могут обмениваться данными только с исходной базой (базами) данных Oracle и целевым экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в качестве клиентов. Они не занимаются активным прослушиванием какого-либо сетевого или иного протокола. Служба Oracle CDC Service отслеживает изменения конфигурации баз данных CDC и обновляет свою работу с учетом обновленной конфигурации.  
  
  
