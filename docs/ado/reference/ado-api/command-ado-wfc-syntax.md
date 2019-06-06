---
title: Команда (ADO — синтаксис WFC) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Command collection [ADO], ADO/WFC syntax
ms.assetid: 39d0aa06-03ac-4c9a-8400-83947756ef99
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 857b5c636cf3d86e2996284c877736114495daf8
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66695833"
---
# <a name="command-ado---wfc-syntax"></a>Command (ADO — синтаксис WFC)
## <a name="package-commswfcdata"></a>com.ms.wfc.data пакета  
  
### <a name="constructor"></a>Конструктор  
  
```  
public Command()  
public Command(String commandtext)  
```  
  
### <a name="methods"></a>Методы  
  
```  
public void cancel()  
public com.ms.wfc.data.Parameter createParameter(String  
    Name, int Type, int Direction, int Size, Object Value)  
public Recordset execute()  
public Recordset execute(Object[] parameters)  
public Recordset execute(Object[] parameters, int options)  
public int executeUpdate(Object[] parameters)  
public int executeUpdate(Object[] parameters, int options)  
public int executeUpdate()  
```  
  
 **ExecuteUpdate** метод — это специальный метод вариантов, который вызывает базовый ADO **выполнение** метод с помощью определенных параметров. **ExecuteUpdate** метод не поддерживает возврат **записей** объекта, поэтому **выполнение** метода *параметры* параметр было изменено с добавлением **AdoEnums.ExecuteOptions.NORECORDS**. После **выполнение** метод завершения, его обновленную *RecordsAffected* параметр передается обратно в **executeUpdate** метод, который возвращается как Наконец**int**.  
  
### <a name="properties"></a>Свойства  
  
```  
public com.ms.wfc.data.Connection getActiveConnection()  
public void setActiveConnection(com.ms.wfc.data.Connection con)  
public void setActiveConnection(String conString)  
public String getCommandText()  
public void setCommandText(String command)  
public int getCommandTimeout()  
public void setCommandTimeout(int timeout)  
public int getCommandType()  
public void setCommandType(int type)  
public String getName()  
public void setName(String name)  
public boolean getPrepared()  
public void setPrepared(boolean prepared)  
public int getState()  
public com.ms.wfc.data.Parameter getParameter(int n)  
public com.ms.wfc.data.Parameter getParameter(String n)  
public com.ms.wfc.data.Parameters getParameters()  
public AdoProperties getProperties()  
```  
  
## <a name="see-also"></a>См. также  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)
