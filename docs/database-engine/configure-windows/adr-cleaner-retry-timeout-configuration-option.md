---
title: " Параметр конфигурации \"Время ожидания повторных попыток очистки ADR (мин)\" | Документация Майкрософт"
description: Описание параметра конфигурации экземпляра SQL Server, задающего время ожидания повторных попыток очистки ADR.
ms.custom: ''
ms.date: 06/01/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- ADR cleaner retry timeout (min)
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 25d7df032b0606a324d98d14258cbbd40602bae7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85698156"
---
# <a name="adr-cleaner-retry-timeout-min-configuration-option"></a>Параметр конфигурации ADR cleaner retry timeout (min) (Время ожидания повторных попыток очистки ADR [мин])

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Впервые представлен в SQL Server 2019.

Этот параметр конфигурации необходим для [ускоренного восстановления баз данных](../../relational-databases/accelerated-database-recovery-concepts.md). Очистка — это асинхронный процесс, который периодически активируется и очищает ненужные версии страниц.

Иногда средство очистки сталкивается с проблемами, связанными с возникновением блокировок на уровне объекта из-за конфликтов с пользовательской рабочей нагрузкой во время выполнения очистки. Оно отслеживает такие страницы в отдельном списке. Параметр "Время ожидания повторных попыток очистки ADR" (значение по умолчанию 15) определяет время, которое средство удаления будет тратить только на попытки получения блокировки объекта и очистки страницы, прежде чем отказаться от очистки. Очистка должна быть завершена со стопроцентно успешным результатом, чтобы не росло количество прерванных транзакций в карте прерванных транзакций. Если не удается очистить отдельный список в течение заданного времени ожидания, текущая очистка будет прервана и начнется следующая очистка.

## <a name="remarks"></a>Remarks  

Процесс очистки в SQL Server 2019 однопотоковый, поэтому в каждый момент времени один экземпляр SQL Server может работать с одной базой данных. Если в экземпляре имеется несколько пользовательских баз данных с включенным правилом автоматического развертывания (ADR), то не следует увеличивать время ожидания, так как это может привести к задержке очистки в одной базе данных, пока происходит повторная попытка в другой базе данных.

## <a name="examples"></a>Примеры

В следующих примерах задается время ожидания повторных попыток очистки.

```tsql
sp_configure 'show advanced options', 1;  
RECONFIGURE;
GO 
sp_configure 'ADR cleaner retry timeout', 15;  
RECONFIGURE;  
GO  
```  

## <a name="see-also"></a>См. также:  

- [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)
- [Ускоренное восстановление баз данных](../../relational-databases/accelerated-database-recovery-concepts.md)
- [Управление ускоренным восстановлением баз данных](../../relational-databases/accelerated-database-recovery-management.md)