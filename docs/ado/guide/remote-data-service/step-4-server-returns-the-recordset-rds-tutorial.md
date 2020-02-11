---
title: Шаг 4. сервер возвращает набор записей (учебник по RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], server returns Recordset
ms.assetid: 3d1855c4-419c-4810-b5ea-6c874b5e2905
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3bd243b21b7003c524c3483f5b8d7bb92be1e18d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922061"
---
# <a name="step-4-server-returns-the-recordset-rds-tutorial"></a>Шаг 4. Сервер возвращает набор записей (учебник по RDS)
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 RDS преобразует полученный объект **набора записей** в форму, которая может быть отправлена обратно клиенту (то есть *маршалирует* **набор записей**). Точный вид преобразования и способ его отправки зависит от того, находится ли сервер в Интернете или интрасети, в локальной сети или в виде библиотеки динамической компоновки. Однако эта информация не является критической. все, что важно, это то, что RDS отправляет **набор записей** обратно клиенту.  
  
 На стороне клиента объект **набора записей** возвращается и назначается локальной переменной.  
  
```vb
Sub RDSTutorial4()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "https://yourServer")  
   Set RS = DF.Query("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>См. также:  
 [Шаг 5. Использование элемента управления "Управление доступом" (руководство по RDS)](../../../ado/guide/remote-data-service/step-5-datacontrol-is-made-usable-rds-tutorial.md)   
 [Учебник по RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
