---
title: Задание параметра максимальной степени параллелизма для оптимальной производительности | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 794dfea63b193ff79fb5831cb3a4e519d7d5f63e
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53351605"
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a>Задание параметра максимальной степени параллелизма для оптимальной производительности
  Это правило определяет, является ли значение параметра максимальной степени параллелизма (MAXDOP) больше 8. Установка большего значения часто приводит к неэффективному расходованию ресурсов и снижению производительности.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Установите значение параметра максимальной степени параллелизма равным 8 или меньше с помощью хранимой процедуры sp_configure.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Статья 329204 базы знаний Майкрософт](https://go.microsoft.com/fwlink/?linkid=117786)  
  
 [Настройка параметра конфигурации сервера max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)  
  
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
