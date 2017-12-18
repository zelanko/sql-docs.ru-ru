---
title: "Проверка на наличие проблем повторного чтения в подсистеме дискового ввода-вывода | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: cedf4097-5b73-4964-9935-74a101847019
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 48624f64233a37be0f1d1c2dc5ad0be6b323cfe6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="check-disk-input-output-subsystem-for-read-retry-problems"></a>Проверка на наличие проблем повторного чтения в подсистеме дискового ввода-вывода
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Это правило проверяет журнал событий на наличие сообщения об ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с кодом 825. Это сообщение показывает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удалось считать данные с диска с первой попытки. Оно указывает на серьезную проблему в подсистеме дискового ввода-вывода. Это сообщение не указывает на текущую проблему [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Однако проблема подсистемы дискового ввода-вывода может привести к потере данных или повреждению базы данных, если она не будет решена.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Следующие действия помогут обнаружить и исправить базовую проблему оборудования.  
  
-   Просмотрите журнал ошибок и переменный текст данного сообщения, объясняющие суть проблемы.  
  
-   Проверьте дисковую систему. Проблема может быть связана с жесткими дисками, контроллерами дисков, контроллерами дисковых массивов или драйверами дисков.  
  
-   Обратитесь к производителю диска за новейшими утилитами проверки состояния дисковой системы.  
  
-   Обратитесь к производителю диска за новейшими обновлениями драйверов.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [MSSQLSERVER_825](http://msdn.microsoft.com/library/f69f8214-5af1-4769-878b-117ad6eaff52)  
  
 [Основные операции ввода-вывода в SQL Server, раздел 2](http://go.microsoft.com/fwlink/?linkid=69370)  
  
  
