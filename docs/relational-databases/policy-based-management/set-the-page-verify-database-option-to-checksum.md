---
title: Задание значения CHECKSUM для параметра базы данных PAGE_VERIFY | Документация Майкрософт
description: Сведения о проверке того, имеет ли параметр PAGE_VERIFY значение CHECKSUM, что определяет, будет ли ядро СУБД SQL Server рассчитывать контрольную сумму для обеспечения целостности файлов данных.
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 5f296dc9aedf96c3258dc256d9bc8fc8fdf05f12
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774172"
---
# <a name="set-the-page_verify-database-option-to-checksum"></a>Задание значения CHECKSUM для параметра базы данных PAGE_VERIFY
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Это правило проверяет, имеет ли параметр базы данных PAGE_VERIFY значение CHECKSUM. Если для параметра базы данных PAGE_VERIFY указано значение CHECKSUM, компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] рассчитывает контрольную сумму для содержимого страницы в целом и сохраняет значение в заголовке страницы при записи страницы на диск. При считывании страницы с диска контрольная сумма вычисляется повторно и сравнивается со значением из заголовка. Это помогает обеспечить высокий уровень целостности данных в файлах.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Присвойте параметру базы данных PAGE_VERIFY значение CHECKSUM  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Параметры ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  
