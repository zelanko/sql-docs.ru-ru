---
title: Проверка на наличие проблем повторного чтения в подсистеме дискового ввода-вывода | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: cedf4097-5b73-4964-9935-74a101847019
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 30d264f29716d954e0b627e1b3ce14c34de86660
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40410076"
---
# <a name="check-disk-input-output-subsystem-for-read-retry-problems"></a>Проверка на наличие проблем повторного чтения в подсистеме дискового ввода-вывода
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это правило проверяет журнал событий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на наличие сообщения об ошибке 825. Это сообщение показывает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удалось считать данные с диска с первой попытки. Оно указывает на серьезную проблему в подсистеме дискового ввода-вывода. Это сообщение не указывает на текущую проблему [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Однако проблема подсистемы дискового ввода-вывода может привести к потере данных или повреждению базы данных, если она не будет решена.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Следующие действия помогут обнаружить и исправить базовую проблему оборудования.  
  
-   Просмотрите журнал ошибок и переменный текст данного сообщения, объясняющие суть проблемы.  
  
-   Проверьте дисковую систему. Проблема может быть связана с жесткими дисками, контроллерами дисков, контроллерами дисковых массивов или драйверами дисков.  
  
-   Обратитесь к производителю диска за новейшими утилитами проверки состояния дисковой системы.  
  
-   Обратитесь к производителю диска за новейшими обновлениями драйверов.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [MSSQLSERVER_825](../errors-events/mssqlserver-825-database-engine-error.md)  
  
 [Основные операции ввода-вывода в SQL Server, раздел 2](http://go.microsoft.com/fwlink/?linkid=69370)  
  
  
