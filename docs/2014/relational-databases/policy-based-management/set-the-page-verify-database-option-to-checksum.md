---
title: Задание значения CHECKSUM для параметра базы данных PAGE_VERIFY | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fb7e0f5db0052b4eaac527a81a7825be2da16df0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099977"
---
# <a name="set-the-pageverify-database-option-to-checksum"></a>Задание значения CHECKSUM для параметра базы данных PAGE_VERIFY
  Это правило проверяет, имеет ли параметр базы данных PAGE_VERIFY значение CHECKSUM. Если для параметра базы данных PAGE_VERIFY указано значение CHECKSUM, компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] рассчитывает контрольную сумму для содержимого страницы в целом и сохраняет значение в заголовке страницы при записи страницы на диск. При считывании страницы с диска контрольная сумма вычисляется повторно и сравнивается со значением из заголовка. Это помогает обеспечить высокий уровень целостности данных в файлах.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Присвойте параметру базы данных PAGE_VERIFY значение CHECKSUM  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Параметры ALTER DATABASE SET (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
