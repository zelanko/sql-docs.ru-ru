---
title: Соединение с сервером Oracle (страница "Свойства соединения") | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.connectionprops.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 479b0d562ffb78bc0003ca320eea0a85ab172430
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62721698"
---
# <a name="connect-to-server-oracle-connection-properties"></a>Соединение с сервером (Oracle), свойства соединения
  Вкладка **Свойства соединения** диалогового окна **Соединение с сервером** позволяет задать параметры публикации **Шлюз** или **Полный**. После идентификации издателя изменить данный параметр без удаления и перенастройки издателя невозможно. Дополнительные сведения см. в статье [Настройка издателя Oracle](non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Параметры  
 **Тип издателя**  
 Выберите **Шлюз** или **Полный**. Параметр **Complete** предназначен для создания моментальных снимков и публикаций транзакций с полным набором поддерживаемых функций для публикации Oracle. Параметр **Шлюз** оптимизирует работу системы для случаев, когда шлюзом между системами выступает репликация. Параметр **Шлюз** нельзя использовать, если одна и та же таблица будет публиковаться в нескольких публикациях транзакций. Если выбран параметр **Шлюз**, то таблица может использоваться только в одной публикации транзакций и в любом количестве публикаций моментальных снимков.  
  
 **Время ожидания**  
 Укажите, как долго [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] распространитель должен пытаться подключиться к издателю Oracle, прежде чем произойдет ошибка времени ожидания.  
  
## <a name="see-also"></a>См. также:  
 [Глоссарий терминов для публикации Oracle](non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Настройка производительности для издателей Oracle](non-sql/performance-tuning-for-oracle-publishers.md)  
  
  
