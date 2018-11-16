---
title: Работа с аспектами управления на основе политик | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- viewing Policy-Based Management facets
- facets [Policy-Based Management], copying
- facets [Policy-Based Management], viewing
- copying Policy-Based Management facets
ms.assetid: 88d025c4-07c2-4e4d-8634-204249a8c82c
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 6893d6d86066cd77d1889ac859c67b0074d6d8c7
ms.sourcegitcommit: ef6e3ec273b0521e7c79d5c2a4cb4dcba1744e67
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2018
ms.locfileid: "51512075"
---
# <a name="working-with-policy-based-management-facets"></a>Работа с аспектами управления на основе политик
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Аспект управления на основе политик — это ряд логических свойств, которые связаны с определенной областью, представляющей интерес с точки зрения управления. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] включает несколько стандартных аспектов. Например, средство настройки контактной зоны, определяющее функции, отключенные по умолчанию.  
  
 При управлении несколькими похожими средами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно настроить аспект в одном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], скопировать состояние аспекта в файл и импортировать этот файл на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в качестве политики. При преобразовании состояния в политику она может быть применена к другим экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], объектам экземпляров, базам данных или объектам баз данных.  
  
 Этот раздел описывает способ копирования состояния аспекта в XML-файл.  
  
##  <a name="BeforeYouBegin"></a> Разрешения  
 Для процедуры в этом разделе требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
## <a name="viewing-and-copying-facet-states"></a>Просмотр и копирование состояний аспекта  
 [Просмотр аспектов управления на основе политик в объекте SQL Server](../../relational-databases/policy-based-management/view-the-policy-based-management-facets-on-a-sql-server-object.md)  
  
 [Копирование состояния аспекта управления на основе политик в XML-файл](../../relational-databases/policy-based-management/copy-a-policy-based-management-facet-state-to-an-xml-file.md)  
  
## <a name="see-also"></a>См. также:  
 [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
