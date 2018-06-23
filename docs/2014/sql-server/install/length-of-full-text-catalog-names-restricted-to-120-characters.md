---
title: Длина имен полнотекстового каталога ограничена 120 символами | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- full-text catalogs names
ms.assetid: 50633373-83f6-4ed9-99b9-71f92479a14f
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f11c8b5a0698c83846f1570946a551f82a09ab48
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191538"
---
# <a name="length-of-full-text-catalog-names-restricted-to-120-characters"></a>Длина имен полнотекстовых каталогов ограничена 120 символами
  Длина имен полнотекстового каталога ограничена 120 символами в отличие от 128 символов в предыдущих версиях служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="description"></a>Описание  
 Это изменение не влияет на существующие имена каталогов, однако скрипты, создающие полнотекстовые каталоги с именами длиннее 120 символов, завершаются с ошибкой. Имена каталогов используются для формирования логических имен файлов, соответствующих каталогу.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Следует изменить все скрипты, создающие полнотекстовые каталоги, чтобы длина имен была ограничена 120 символами.  
  
## <a name="see-also"></a>См. также  
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  