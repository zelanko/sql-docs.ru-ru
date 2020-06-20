---
title: Обновление преобразований «Уточняющий запрос» | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation and upgrading
- upgrading caching for Lookup transformation
- upgrading Lookup transformation
ms.assetid: d9b2c281-91ee-4e20-bdf0-0cd77d4a4241
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 74430ab1bed232b8d510a8c28a8a690d88d1f6ba
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85041652"
---
# <a name="upgrade-lookup-transformations"></a>Обновление преобразований «Уточняющий запрос»
  При обновлении с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] полезно изменить пакеты, чтобы использовать преимущества новых возможностей преобразования «Уточняющий запрос». Это преобразование поддерживает типы кэширования и параметры вывода данных, доступные в службах [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]. Дополнительные сведения о дополнительном кэшировании и выводе данных см. в разделе [Lookup Transformation](../../integration-services/data-flow/transformations/lookup-transformation.md).  
  
 В службах [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]доступными типами кэширования являются полное кэширование, частичное кэширование и отсутствие кэширования. В службах [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]можно настроить преобразование «Уточняющий запрос» для использования одного из этих типов кэширования. Дополнительные сведения о реализации частичного кэширования или отсутствии кэширования см. [в разделе Реализация поиска без кэширования или режим частичного кэширования](../../integration-services/data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md). Сведения о реализации полного кэширования см. в разделе [Реализация преобразования «Уточняющий запрос» в режиме полного кэширования с помощью диспетчера соединений с кэшем](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md) и [Реализация преобразования «Уточняющий запрос» в режиме полного кэширования с помощью диспетчера соединений OLE DB](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md).  
  
 В [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]преобразование «Уточняющий запрос» характеризуется применением потоков ввода, вывода, а также вывода ошибок. Строки в потоке ввода, для которых имеются совпадающие записи в эталонном наборе данных, обрабатываются в потоке вывода. Строки в потоке ввода, для которых совпадающие записи отсутствуют, рассматриваются как ошибочные и могут быть перенаправлены в поток вывода ошибок. В службах [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]преобразование «Уточняющий запрос» имеет два выхода: выход совпадающих строк и выход несовпадающих строк.  
  
 По умолчанию при выполнении преобразования «Уточняющий запрос», созданного в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], строки без совпадающих записей рассматриваются в [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] как ошибочные, и разрешается перенаправлять эти строки в выход ошибок. Предусмотрена возможность так настроить преобразование «Уточняющий запрос», чтобы эти строки рассматривались как не имеющие ошибок и перенаправлялись в выход несовпадающих строк.  
  
 Дополнительные сведения см. в разделе [Редактор преобразования "Уточняющий запрос" &#40;общие&#41;страницы ](../../integration-services/general-page-of-integration-services-designers-options.md).  
  
## <a name="see-also"></a>См. также:  
 [Преобразование "Уточняющий запрос"](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  
