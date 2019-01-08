---
title: Проверка на наличие проблем повторного чтения подсистеме ввода-вывода диска | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: cedf4097-5b73-4964-9935-74a101847019
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1072668681a7e989e0ebb1bbcc385cc53e5a7b2d
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53362416"
---
# <a name="check-disk-input-output-subsystem-for-read-retry-problems"></a>Проверка на наличие проблем повторного чтения в подсистеме дискового ввода-вывода
  Это правило проверяет журнал событий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на наличие сообщения об ошибке 825. Это сообщение показывает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удалось считать данные с диска с первой попытки. Оно указывает на серьезную проблему в подсистеме дискового ввода-вывода. Это сообщение не указывает на текущую проблему [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Однако проблема подсистемы дискового ввода-вывода может привести к потере данных или повреждению базы данных, если она не будет решена.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Следующие действия помогут обнаружить и исправить базовую проблему оборудования.  
  
-   Просмотрите журнал ошибок и переменный текст данного сообщения, объясняющие суть проблемы.  
  
-   Проверьте дисковую систему. Проблема может быть связана с жесткими дисками, контроллерами дисков, контроллерами дисковых массивов или драйверами дисков.  
  
-   Обратитесь к производителю диска за новейшими утилитами проверки состояния дисковой системы.  
  
-   Обратитесь к производителю диска за новейшими обновлениями драйверов.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [MSSQLSERVER_825](../errors-events/mssqlserver-825-database-engine-error.md)  
  
 [Основные операции ввода-вывода в SQL Server, раздел 2](https://go.microsoft.com/fwlink/?linkid=69370)  
  
  
