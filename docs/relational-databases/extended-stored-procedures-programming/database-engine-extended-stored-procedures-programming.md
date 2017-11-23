---
title: "Программирование расширенных хранимых процедур | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- gateway applications [SQL Server]
- extended stored procedures [SQL Server], about extended stored procedures
- Open Data Services [SQL Server]
- ODS [SQL Server]
ms.assetid: 561305cd-c803-48af-9eec-2c19f4d311ce
caps.latest.revision: "42"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0bc18c61895dcd92903881be35e920ab969cfb70
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="database-engine-extended-stored-procedures---programming"></a>Компонент Database Engine расширенные хранимые процедуры - программирование
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Вместо этого используйте интеграцию со средой CLR.  
  
 В прошлом службы Open Data Services использовались для создания серверных приложений, таких как шлюзы к СУБД, отличных от SQL Server. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает устаревшие фрагменты API служб Open Data. Единственная часть исходного API-интерфейса служб Open Data Services, все еще поддерживаемая [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], это функции расширенных хранимых процедур, поэтому API-интерфейс был переименован в API-интерфейс расширенных хранимых процедур.  
  
 После возникновения более новых и более мощных технологий, таких как распределенные запросы и интеграция со средой CLR, потребность в приложениях API-интерфейса расширенных хранимых процедур значительно снизилась.  
  
> [!NOTE]  
>  При наличии существующих приложений шлюзов нельзя использовать библиотеку opends60.dll, поставляемую с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], для запуска приложений. Приложения шлюзов больше не поддерживаются.  
  
## <a name="extended-stored-procedures-vs-clr-integration"></a>Расширенные хранимые процедуры и Интеграция со средой CLR.  
 В более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] расширенные хранимые процедуры представляли собой единственный доступный механизм, позволяющий разработчикам баз данных создавать логику на стороне сервера, которую трудно или невозможно написать с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]. Интеграция со средой CLR более надежна, чем использование таких хранимых процедур. Более того, благодаря интеграции со средой CLR, логика, ранее создаваемая в виде хранимых процедур, зачастую лучше выражается возвращающими табличные значения функциями, что позволяет выполнять к результатам такой функции запросы в виде инструкций SELECT, внедряя их в предложение FROM.  
  
## <a name="see-also"></a>См. также:  
 [Общеязыковая среда выполнения &#40; Среда CLR &#41; Общие сведения об интеграции](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md)   
 [Функции среды CLR, возвращающие табличное значение](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-table-valued-functions.md)  
  
  
