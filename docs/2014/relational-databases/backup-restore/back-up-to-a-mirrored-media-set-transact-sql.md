---
title: Создание резервной копии на зеркальном наборе носителей (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 88ea15fabe8e8fd6630d3430417879c7104dff67
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62876992"
---
# <a name="back-up-to-a-mirrored-media-set-transact-sql"></a>Создание резервной копии на зеркальном наборе носителей (Transact-SQL)
  В этой статье описано, как использовать инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql), чтобы указать зеркальный набор носителей при резервном копировании базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для определения зеркального набора носителей в инструкции BACKUP укажите первое зеркало в предложении TO. Затем определите каждое зеркало в своем собственном предложении TO. Предложения TO и MIRROR TO должны определять одинаковое количество и одинаковый тип устройств резервного копирования.  
  
## <a name="example"></a>Пример  
 В следующем примере создается зеркальный набор носителей, показанный на предыдущем рисунке, и производится резервное копирование базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] на оба зеркала.  
  
```  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH  
    FORMAT,  
    MEDIANAME = 'AdventureWorks2012Set1';  
GO  
```  
  
## <a name="related-tasks"></a>Связанные задачи  
 **Восстановление из зеркальной резервной копии**  
  
-   [Восстановление &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
## <a name="see-also"></a>См. также:  
 [&#41;BACKUP &#40;Transact-SQL](/sql/t-sql/statements/backup-transact-sql)   
 [Зеркальные наборы носителей резервных копий &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)  
  
  
