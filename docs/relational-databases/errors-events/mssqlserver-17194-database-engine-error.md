---
title: MSSQLSERVER_17194 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
f1_keywords:
- "17194"
helpviewer_keywords:
- 17194 (Database Engine error)
ms.assetid: 0d03eb20-28a7-4ceb-8903-7f9420a620f7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 24dd0f06cd533886b2f26c4dacc857bd9a0b0fe6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780818"
---
# <a name="mssqlserver_17194"></a>MSSQLSERVER_17194
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|17194|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|Серверу не удалось загрузить библиотеку поставщика SSL, необходимую для входа. Соединение было закрыто. С помощью SSL шифруется последовательность входа в систему или весь обмен данными (в зависимости от конфигурации сервера). Дополнительные сведения об этой ошибке см. в электронной документации:  0xXXXX. [Клиент: 11.11.11.11]|  
  
## <a name="explanation"></a>Объяснение  
Эта ошибка означает, что клиент закрыл соединение. Она может возникать по истечении времени ожидания соединения. Эта ошибка возвращает значение, переданное операционной системой. Это значение описывает соответствующую неполадку.  
  
## <a name="user-action"></a>Действие пользователя  
Если в сообщении выведен код ошибки 0x2746 (десятичное значение 10054), то это означает, что соединение было сброшено клиентом. Обычно это происходит при истечении времени ожидания. Для устранения этой ошибки необходимо увеличить время ожидания соединения для клиента или вызывающей программы.  
  
Для определения возможных решений для других значений, выдаваемых сообщением об ошибке, выполните команду **net helpmsg**, указав для нее десятичное значение кода ошибки.  
  
Дополнительные сведения о подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статьях [Сетевая конфигурация сервера](~/database-engine/configure-windows/server-network-configuration.md) и [Конфигурация клиентской сети](~/database-engine/configure-windows/client-network-configuration.md).  
  
## <a name="internal-only"></a>Только для внутреннего использования  
