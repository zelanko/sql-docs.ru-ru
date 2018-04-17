---
title: Контекстное соединение | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context connections [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- context [CLR integration]
ms.assetid: 67dd1925-d672-4986-a85f-bce4fe832ef7
caps.latest.revision: 13
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6102bb4ec20354d11573cb94e56d00c2d6641da2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="context-connection"></a>Контекстное соединение
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Проблема внутреннего доступа к данным встречается довольно часто. Речь идет о тех ситуациях, когда необходимо получить доступ к тому же серверу, на котором выполняется конкретная хранимая процедура или функция среды CLR. Один из вариантов является создание соединения с помощью **System.Data.SqlClient.SqlConnection**, укажите строку подключения, которая указывает на локальном сервере и открытия соединения. В этом случае требуется указать учетные данные для входа в систему. Подключение в сеансе другую базу данных по сравнению с хранимой процедурой или функцией, оно может иметь другие **ЗАДАТЬ** параметры, он находится в отдельной транзакции, не позволяет обнаруживать используемые временные таблицы и т. д. Если управляемая хранимая процедура или функция выполняется в процессе SQL Server, причина этого состоит в том, что кто-то соединился с этим сервером и выполнил инструкцию SQL для вызова соответствующего процедуры или функции. Требуется, вероятно, хранимая процедура или функция, выполняемая в контексте данного соединения вместе с его транзакции **ЗАДАТЬ** параметры и т. д. В этом состоит так называемое контекстное соединение.  
  
 Контекстное соединение позволяет выполнять инструкции Transact-SQL в том же контексте, в каком первоначально был вызван конкретный код. Для получения контекстного соединения необходимо использовать ключевое слово «context connection» строки соединения, как в примере ниже:  
  
 [C#]  
  
```  
using(SqlConnection connection = new SqlConnection("context connection=true"))   
{  
    connection.Open();  
    // Use the connection  
}  
```  
  
 [Visual Basic]  
  
```  
Using connection as new SqlConnection("context connection=true")  
    connection.Open()  
    ' Use the connection  
End Using  
  
```  
  
## <a name="in-this-section"></a>В этом разделе  
 [Регулярные vs. Контекстные соединения](../../../relational-databases/clr-integration/data-access/context-connections-vs-regular-connections.md)  
 Описывает разницу между регулярными и контекстными соединениями.  
  
 [Ограничения обычных и контекстных соединений](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md)  
 Описывает ограничения регулярных и контекстных соединений.  
  
  
