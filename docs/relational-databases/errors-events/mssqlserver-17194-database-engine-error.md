---
title: "MSSQLSERVER_17194 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: "17194"
helpviewer_keywords: 17194 (Database Engine error)
ms.assetid: 0d03eb20-28a7-4ceb-8903-7f9420a620f7
caps.latest.revision: "11"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 437a7afe75e2e87a35deee36b3662efa47d2e339
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver17194"></a>MSSQLSERVER_17194
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17194|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|Серверу не удалось загрузить библиотеку поставщика SSL, необходимую для входа. Соединение было закрыто. С помощью SSL шифруется последовательность входа в систему или весь обмен данными (в зависимости от конфигурации сервера). Дополнительные сведения об этой ошибке см. в электронной документации: 0xXXXX. [CLIENT: 11.11.11.11]|  
  
## <a name="explanation"></a>Объяснение  
Эта ошибка означает, что клиент закрыл соединение. Она может возникать по истечении времени ожидания соединения. Эта ошибка возвращает значение, переданное операционной системой. Это значение описывает соответствующую неполадку.  
  
## <a name="user-action"></a>Действие пользователя  
Если в сообщении выведен код ошибки 0x2746 (десятичное значение 10054), то это означает, что соединение было сброшено клиентом. Обычно это происходит при истечении времени ожидания. Для устранения этой ошибки необходимо увеличить время ожидания соединения для клиента или вызывающей программы.  
  
Для определения возможных решений для других значений, выдаваемых сообщением об ошибке, выполните команду **net helpmsg**, указав для нее десятичное значение кода ошибки.  
  
Дополнительные сведения о подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статьях [Сетевая конфигурация сервера](~/database-engine/configure-windows/server-network-configuration.md) и [Конфигурация клиентской сети](~/database-engine/configure-windows/client-network-configuration.md).  
  
## <a name="internal-only"></a>Только для внутреннего использования  
