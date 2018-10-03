---
title: Контекстное соединение | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f5c7ca551fed96fb9c7149a894ecf78a441592c9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789392"
---
# <a name="context-connection"></a>Контекстное соединение
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Проблема внутреннего доступа к данным встречается довольно часто. Речь идет о тех ситуациях, когда необходимо получить доступ к тому же серверу, на котором выполняется конкретная хранимая процедура или функция среды CLR. Один из вариантов — создать соединение с помощью **System.Data.SqlClient.SqlConnection**, укажите строку соединения, который указывает на локальном сервере и открытия соединения. В этом случае требуется указать учетные данные для входа в систему. Соединение находится в другой базе данных сеанса, а не хранимую процедуру или функцию, может иметь другие **ЗАДАТЬ** параметры, он находится в отдельной транзакции, не позволять обнаруживать используемые временные таблицы, и т. д. Если управляемая хранимая процедура или функция выполняется в процессе SQL Server, причина этого состоит в том, что кто-то соединился с этим сервером и выполнил инструкцию SQL для вызова соответствующего процедуры или функции. Может понадобиться хранимая процедура или функция, выполняемая в контексте данного соединения вместе с его транзакции **ЗАДАТЬ** параметры и т. д. В этом состоит так называемое контекстное соединение.  
  
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
  
## <a name="in-this-section"></a>в этом разделе  
 [Сравнение обычных и контекстных подключений](../../../relational-databases/clr-integration/data-access/context-connections-vs-regular-connections.md)  
 Описывает разницу между регулярными и контекстными соединениями.  
  
 [Ограничения обычных и контекстных подключений](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md)  
 Описывает ограничения регулярных и контекстных соединений.  
  
  
