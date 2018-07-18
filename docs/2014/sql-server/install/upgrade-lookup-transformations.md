---
title: Обновление «Уточняющий запрос» | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation and upgrading
- upgrading caching for Lookup transformation
- upgrading Lookup transformation
ms.assetid: d9b2c281-91ee-4e20-bdf0-0cd77d4a4241
caps.latest.revision: 16
author: mashamsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8da8551b85948f27f1e657cb70c4bb1140c5314b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224802"
---
# <a name="upgrade-lookup-transformations"></a>Обновление преобразований «Уточняющий запрос»
  При обновлении с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] полезно изменить пакеты, чтобы использовать преимущества новых возможностей преобразования «Уточняющий запрос». Это преобразование поддерживает типы кэширования и параметры вывода данных, доступные в службах [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]. Дополнительные сведения о дополнительных кэшировании и выводе данных, см. в разделе [уточняющий](../../integration-services/data-flow/transformations/lookup-transformation.md).  
  
 В службах [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] доступными типами кэширования являются полное кэширование, частичное кэширование и отсутствие кэширования. В службах [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] можно настроить преобразование «Уточняющий запрос» для использования одного из этих типов кэширования. Дополнительные сведения о том, как реализовать частичного кэширования или отсутствия кэширования, см. в разделе [реализация уточняющего запроса в No Cache или в режиме частичного кэширования](../../integration-services/data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md). Сведения о том, как реализовать полное кэширование, см. в разделе [реализовать преобразование «Уточняющий запрос» в полный режиме кэширования с помощью диспетчера соединений с кэшем](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md) и [реализовать преобразование «Уточняющий запрос» в полного кэширования режиме с помощью OLE Диспетчер соединений DB](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md).  
  
 В [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] преобразование «Уточняющий запрос» характеризуется применением потоков ввода, вывода, а также вывода ошибок. Строки в потоке ввода, для которых имеются совпадающие записи в эталонном наборе данных, обрабатываются в потоке вывода. Строки в потоке ввода, для которых совпадающие записи отсутствуют, рассматриваются как ошибочные и могут быть перенаправлены в поток вывода ошибок. В службах [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] преобразование «Уточняющий запрос» имеет два выхода: выход совпадающих строк и выход несовпадающих строк.  
  
 По умолчанию при выполнении преобразования «Уточняющий запрос», созданного в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], строки без совпадающих записей рассматриваются в [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] как ошибочные, и разрешается перенаправлять эти строки в выход ошибок. Предусмотрена возможность так настроить преобразование «Уточняющий запрос», чтобы эти строки рассматривались как не имеющие ошибок и перенаправлялись в выход несовпадающих строк.  
  
 Дополнительные сведения см. в разделе [уточняющий &#40;страница "Общие"&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).  
  
## <a name="see-also"></a>См. также  
 [Преобразование "Уточняющий запрос"](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  
