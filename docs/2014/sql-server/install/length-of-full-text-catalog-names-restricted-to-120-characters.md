---
title: Длина имен полнотекстового каталога ограничена 120 символами | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs names
ms.assetid: 50633373-83f6-4ed9-99b9-71f92479a14f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5cce05426fdff2aacf40612738ad80b07d9ec0e2
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66094063"
---
# <a name="length-of-full-text-catalog-names-restricted-to-120-characters"></a>Длина имен полнотекстовых каталогов ограничена 120 символами
  Длина имен полнотекстового каталога ограничена 120 символами в отличие от 128 символов в предыдущих версиях служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="description"></a>Описание  
 Это изменение не влияет на существующие имена каталогов, однако скрипты, создающие полнотекстовые каталоги с именами длиннее 120 символов, завершаются с ошибкой. Имена каталогов используются для формирования логических имен файлов, соответствующих каталогу.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Следует изменить все скрипты, создающие полнотекстовые каталоги, чтобы длина имен была ограничена 120 символами.  
  
## <a name="see-also"></a>См. также  
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
