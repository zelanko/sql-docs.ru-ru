---
title: "Задание значения CHECKSUM для параметра базы данных PAGE_VERIFY | Документация Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3bd575c72ea39e3f0b0050bfa508913a652d8023
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="set-the-pageverify-database-option-to-checksum"></a>Задание значения CHECKSUM для параметра базы данных PAGE_VERIFY
  Это правило проверяет, имеет ли параметр базы данных PAGE_VERIFY значение CHECKSUM. Если для параметра базы данных PAGE_VERIFY указано значение CHECKSUM, компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] рассчитывает контрольную сумму для содержимого страницы в целом и сохраняет значение в заголовке страницы при записи страницы на диск. При считывании страницы с диска контрольная сумма вычисляется повторно и сравнивается со значением из заголовка. Это помогает обеспечить высокий уровень целостности данных в файлах.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Присвойте параметру базы данных PAGE_VERIFY значение CHECKSUM  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  

