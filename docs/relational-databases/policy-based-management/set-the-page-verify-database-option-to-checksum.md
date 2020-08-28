---
title: Задание значения CHECKSUM для параметра базы данных PAGE_VERIFY | Документация Майкрософт
description: Сведения о проверке того, имеет ли параметр PAGE_VERIFY значение CHECKSUM, что определяет, будет ли ядро СУБД SQL Server рассчитывать контрольную сумму для обеспечения целостности файлов данных.
ms.custom: ''
ms.date: 08/19/2020
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
ms.openlocfilehash: 4dda2b9138882490b1556b9dbb39f71e35767f5f
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646514"
---
# <a name="set-the-page_verify-database-option-to-checksum"></a>Задание значения CHECKSUM для параметра базы данных PAGE_VERIFY
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Это правило проверяет, имеет ли параметр базы данных PAGE_VERIFY значение CHECKSUM. Если для параметра базы данных PAGE_VERIFY указано значение CHECKSUM, компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] рассчитывает контрольную сумму для содержимого страницы в целом и сохраняет значение в заголовке страницы при записи страницы на диск. При считывании страницы с диска контрольная сумма вычисляется повторно и сравнивается со значением из заголовка. Это помогает обеспечить высокий уровень целостности данных в файлах.  Если для базы данных используется параметр PAGE VERIFY CHECKSUM, то, когда SQL Server обнаружит, что страница была изменена после записи на диск, он выдаст сообщение [Msg 824](../errors-events/mssqlserver-824-database-engine-error.md) после считывания страницы с диска. 
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Присвойте параметру базы данных PAGE_VERIFY значение CHECKSUM Параметр базы данных PAGE_VERIFY CHECKSUM — это самый надежный способ обнаружить проблемы согласованности базы данных, вызванные системным путем ввода-вывода.
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Параметры ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  
