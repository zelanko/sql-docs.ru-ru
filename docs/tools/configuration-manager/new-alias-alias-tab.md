---
title: "Создание псевдонима (вкладка «псевдоним») | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 785eb6fb-f67e-449d-b1c8-c38dfbb95ef6
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8a39d7940814839dcda00d45b7dd325a887a3d7b
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="new-alias-alias-tab"></a>Создание псевдонима (вкладка «Псевдоним»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
Псевдоним является альтернативным именем, которое можно использовать для создания соединения. Псевдоним инкапсулирует необходимые элементы строки соединения и представляет их с помощью имени, выбранного пользователем. Используйте страницу **Псевдоним** в диалоговом окне **Псевдоним — новый**, чтобы задать элементы строки подключения для псевдонима. Сведения об изменении строки подключения существующего псевдонима см. в разделе [Свойства &#60;Псевдоним&#62; (вкладка "Псевдоним")](../../tools/configuration-manager/alias-properties-alias-tab.md).  
  
 Необязательно заполнять все значения в сетке **Свойства** . Допустимые сочетания значений зависят от выбранного протокола. Примеры допустимых сочетаний см. в разделах, приведенных ниже.  
  
 **Имя псевдонима**  
 Имя (псевдоним), которое будет использоваться для ссылки на это соединение.  
  
 **Имя канала** / **Номер порта**  
 Дополнительные элементы строки подключения. Имя этого поля зависит от выбранного протокола.  
  
 **Протокол**  
 Протокол, используемый для соединения.  
  
 **Server**  
 Имя экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , к которому выполняется подключение.  
  
## <a name="when-to-use-an-alias"></a>Использование псевдонима  
 По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключается к локальному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью протокола **Общая память** и к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на другом компьютере с помощью протокола **TCP/IP** или **Именованные каналы**. Создайте псевдоним, если во время использования протокола TCP/IP или именованных каналов необходимо вводить пользовательскую строку подключения или если для соединения нужно использовать имя, отличное от имени сервера.  
  
### <a name="examples"></a>Примеры  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не прослушивает установленный по умолчанию порт TCP/IP под номером 1433, поэтому необходимо использовать строку подключения с другим номером порта.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не прослушивает именованный канал по умолчанию, поэтому необходимо использовать строку соединения с другим именем канала.  
  
-   Приложение ожидает подключения к базе данных на сервере с именем `ACCT`, но эта база данных прошла консолидацию в виде экземпляра с именем `ACCT` на сервере с именем `CENTRAL`. Приложение нельзя легко изменить. Создайте псевдоним с именем `ACCT`и со строкой соединения, указывающей на `CENTRAL\ACCT`.  
  
## <a name="creating-a-valid-connection-string"></a>Создание допустимой строки соединения  
 Описание и примеры допустимых сочетаний свойств псевдонима см. в следующих разделах:  
  
-   [Создание допустимой строки соединения с использованием протокола общей памяти](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
-   [Создание допустимой строки соединения с использованием протокола TCP/IP](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
-   [Создание допустимой строки соединения с использованием именованных каналов](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)  
  
  
