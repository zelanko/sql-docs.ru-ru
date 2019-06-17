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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62771497"
---
# <a name="change-data-capture-service-for-oracle-by-attunity-system-architecture"></a>Архитектура службы системы отслеживания измененных данных для Oracle компании Attunity
  Служба CDC Service для Oracle отслеживает изменения выбранных таблиц из одной или нескольких исходных баз данных Oracle и записывает сведения о них в базы данных CDC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , расположенные в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . На следующей диаграмме показаны компоненты, составляющие службу CDC Service для Oracle.  
  
 ![Архитектура службы](../media/service-architecture.gif "Архитектура службы")  
  
 На рисунке показано использование четырех платформ. Во многих случаях эти платформы могут дублировать друг друга, однако на диаграмме представлен стандартный вариант использования. Например, часто бывает целесообразно, чтобы Oracle и базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выполнялись на разных компьютерах, а не совместно с платформой службы Oracle CDC Service или платформой, с которой запускается служба CDC Service. На этом рисунке показаны следующие платформы:  
  
-   Служба Oracle CDC Service. Это может быть любой поддерживаемый компьютер с ОС Windows, где установлена и запущена служба Oracle CDC Service. Эта платформа может также представлять собой узел в отказоустойчивом кластере Microsoft (конфигурации высокого уровня доступности описаны далее в этом документе).  
  
-   База данных Oracle Database. Это может быть любой компьютер, на котором работает поддерживаемая версия базы данных Oracle. Сюда входят любые компьютеры, работающие под управлением ОС Windows, Linux или любой другой операционной системы, поддерживаемой версией установленной базы данных Oracle. Следует отметить, что на диаграмме показано несколько таких платформ, поскольку одна служба Oracle CDC Service может отслеживать изменения в нескольких исходных базах данных Oracle.  
  
-   Экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Это может быть любой компьютер, на котором работает целевая база данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (поддерживаемый номер SKU [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]). Служба Oracle CDC Service поддерживает один целевой экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , где хранятся таблицы изменений и конфигурация службы. Платформа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может также представлять собой кластеризованный экземпляр [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] или зеркалированный экземпляр [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с функцией **AlwaysOn** .  
  
-   Конструктор Oracle CDC Designer. Это может быть любой поддерживаемый компьютер с ОС Windows, который может осуществлять доступ к исходной базе данных Oracle и целевой базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 В следующей таблице описаны компоненты, которые выполняются на четырех платформах, указанных выше.  
  
|Компонент/Описание|Компонент включает в себя следующее:|  
|----------------------------|----------------------------|  
|Служба Oracle CDC Service. Это служба Windows, которая выполняет действия по отслеживанию измененных данных.|Экземпляр Oracle CDC Instance. Подпроцесс службы Oracle CDC Service, который обрабатывает действия по отслеживанию измененных данных для одной исходной базы данных Oracle (на одну исходную базу данных Oracle приходится один экземпляр Oracle CDC).<br /><br /> Средство чтения журнала Oracle Log Reader. Читает журналы транзакций Oracle с помощью клиента Oracle Client.<br /><br /> Клиент Oracle Client. Клиент Oracle Instant Client, используемый для обмена данными с Oracle. Это обязательный компонент, который нужно получить у Oracle и установить до установки службы Oracle CDC Service.<br /><br /> Средство записи изменений [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Выполняет запись зафиксированных изменений, внесенных в отслеживаемые таблицы Oracle, в таблицы изменений [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Этот компонент также поддерживает состояние отслеживания в целевой базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .<br /><br /> Клиент ODBC[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Собственный клиент Microsoft Native Client для [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Это обязательный компонент, который нужно получить у Microsoft и установить до установки службы Oracle CDC Service.|  
|Конфигурация службы Oracle CDC Service. Это оснастка консоли управления (MMC), которая создает службу Windows и настраивает ее конфигурацию.|Клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Клиент SQL ADO.NET, который поставляется с платформой .NET Framework версии 4.|  
|База данных Oracle Database. Исходная база данных Oracle, в которой отслеживаются изменения выбранных таблиц.|Средство интеллектуального анализа журнала Log Miner. Компонент Oracle, с помощью которого читаются журналы транзакций Oracle.<br /><br /> Журналы транзакций. Активные и архивированные журналы операций повтора Oracle Redo Logs, используемые Oracle для отката транзакций и восстановления после сбоев (в этом случае база данных Oracle должна работать в режиме ARCHIVELOG).|  
|Экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], где размещаются базы данных CDC. Это может быть кластеризованный экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (отказоустойчивый кластер) или зеркальная база данных (с функцией AlwaysOn).|База данных MSXDBCDC. База данных, в которой хранятся сведения о службах CDC Service, работающих с этим экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Здесь также хранятся сведения об экземплярах Oracle CDC, обрабатываемых каждой службой CDC Service. Эта база данных создается в ходе процесса создания службы CDC Service.<br /><br /> Базы данных CDC. Базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , в которых хранятся изменения одной из баз данных-источников Oracle. В базах данных CDC обеспечена возможность работы CDC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , поэтому у них есть таблицы и функции CDC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , облегчающие прием данных об изменениях, получаемых из Oracle.|  
|Конструктор Oracle CDC Designer. Оснастка консоли управления (MMC), которая позволяет создавать экземпляры Oracle CDC. Используется для выбора таблиц и столбцов, в которых будут отслеживаться изменения, указания данных подключения к Oracle и управления жизненным циклом экземпляров CDC.|Клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Клиент SQL ADO.NET, который поставляется с платформой .NET Framework версии 4.<br /><br /> Клиент Oracle Client. Клиент Oracle Instant Client, используемый для обмена данными с Oracle. Это обязательный компонент, который нужно получить у Oracle и установить до установки службы Oracle CDC Service.|  
  
 Служба Oracle CDC Service и ее дочерние экземпляры Oracle CDC могут обмениваться данными только с исходной базой (базами) данных Oracle и целевым экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в качестве клиентов. Они не занимаются активным прослушиванием какого-либо сетевого или иного протокола. Служба Oracle CDC Service отслеживает изменения конфигурации баз данных CDC и обновляет свою работу с учетом обновленной конфигурации.  
  
  
