---
title: MSSQLSERVER_17194 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- "17194"
helpviewer_keywords:
- 17194 (Database Engine error)
ms.assetid: 0d03eb20-28a7-4ceb-8903-7f9420a620f7
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f1fb5a0f65e26299346d114e6e38d1739a38b455
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver17194"></a>MSSQLSERVER_17194
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
