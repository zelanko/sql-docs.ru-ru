---
title: Объект DataControl (RDS) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DataControl
- RDS.DataControl
helpviewer_keywords:
- DataControl object [ADO]
ms.assetid: d85ea4fc-451c-436e-97b8-58f92b149dd0
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c1ca22f1a9573ba9f3e01a557eb64f2cb5f4f841
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="datacontrol-object-rds"></a>Объект DataControl (RDS)
Привязывает запрос данных [записей](../../../ado/reference/ado-api/recordset-object-ado.md) для одного или нескольких элементов управления (например, текстовое поле, элемент управления DataGrid или поле со списком) для отображения **записей** данных на веб-странице.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DataControl"  
   <PARAM NAME="Connect" VALUE="DSN=DSNName;UID=MyUserID;PWD=MyPassword;">  
   <PARAM NAME="Server" VALUE="http://awebsrvr">  
   <PARAM NAME="SQL" VALUE="QueryText">  
</OBJECT>  
```  
  
## <a name="remarks"></a>Замечания  
 Идентификатор класса для **RDS. DataControl** BD96C556 65A3 - 11 D 0-983A-00C04FC29E33 является объект.  
  
> [!NOTE]
>  Если вы получаете сообщение об [RDS. Пространство данных](../../../ado/reference/rds-api/dataspace-object-rds.md) или **RDS. DataControl** объекта не загрузить, убедитесь, что вы используете правильный класс идентификатор. Класс из версии 1.0 и 1.1 изменены идентификаторы для этих объектов. Также следует помнить, что даже допускает значения NULL столбцов должен быть установлен, при использовании **DataControl служб удаленных рабочих СТОЛОВ** объекта.  
  
 Основные сценарии, необходимо задать только **SQL**, **Connect**, и **сервера** свойства **RDS. DataControl** объекта, который будет автоматически вызывать бизнес-объекта по умолчанию, [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md).  
  
 Все свойства в **RDS. DataControl** являются необязательными, так как настраиваемые бизнес-объекты можно заменить их функциональность.  
  
> [!NOTE]
>  При выполнении запроса для нескольких результатов только первые [записей](../../../ado/reference/ado-api/recordset-object-ado.md) возвращается. Если требуется несколько результирующих наборов, назначьте каждому свой собственный **DataControl**. Пример запроса для нескольких результатов может выглядеть следующим образом: `"Select * from Authors, Select * from Topics"`  
  
 Добавление «DFMode = 20;» в строке подключения при использовании **RDS. DataControl** объекта может повысить производительность сервера, при обновлении данных. Этот параметр **RDSServer.DataFactory** объект на сервере использует режим менее ресурсоемки. Тем не менее следующие функции будут недоступны в этой конфигурации.  
  
-   Использование параметризованных запросов.  
  
-   Получение сведений о параметра или столбца перед вызовом **Execute** метод.  
  
-   Установка **Transact обновления** для **True**.  
  
-   Получение строки состояния.  
  
-   Вызов [Resync](../../../ado/reference/ado-api/resync-method.md) метод.  
  
-   Обновление (явно или автоматически) через [обновление Resync](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) свойство.  
  
-   Установка **команда** или [записей](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) свойства.  
  
-   С помощью **adCmdTableDirect**.  
  
 **RDS. DataControl** объект выполняется в асинхронном режиме по умолчанию. Если требуется синхронное выполнение приложения задайте [ExecuteOptions](../../../ado/reference/rds-api/executeoptions-property-rds.md) параметра равно **adcExecSync** и [FetchOptions](../../../ado/reference/rds-api/fetchoptions-property-rds.md) параметра равно **adcFetchUpFront**, как показано в следующем примере.  
  
```  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"   
    ID="DataControl"  
   <PARAM NAME="Connect" VALUE="DSN=DSNName;UID=MyUserID;PWD=MyPassword;">  
   <PARAM NAME="Server" VALUE="http://awebsrvr">  
   <PARAM NAME="SQL" VALUE="QueryText">  
   <PARAM NAME="ExecuteOptions" VALUE="1">   <PARAM NAME="FetchOptions" VALUE="1">  
</OBJECT>  
```  
  
 Используйте один **RDS. DataControl** объекта для связывания одного или нескольких элементов управления visual результаты одного запроса. Предположим, например, код запроса запрашивает данные клиента, такие как имя, проживания, место рождения, возраст и состояние клиента с приоритетом. Можно использовать отдельный **RDS. DataControl** объекта для отображения имени клиента, возраст и регион в три отдельные текстовые поля; Состояние клиента приоритета флажок; и все данные в элемент управления DataGrid.  
  
 Использование разных **RDS. DataControl** объектов для ссылки на различные элементы управления visual результатов нескольких запросов. Например предположим, что используется один запрос для получения сведений о клиенте, а второй запрос для получения сведений о товаров, приобретенных клиентом. Вы хотите отобразить результаты первого запроса на три текстовых поля и флажки и результаты второго запроса в сетку. Если вы используете бизнес-объекта по умолчанию (**RDSServer.DataFactory**), необходимо выполнить следующие действия:  
  
-   Добавление двух **RDS. DataControl** объектов на веб-страницу.  
  
-   Запрашивает две записи, один для каждого **SQL** свойства двух **RDS. DataControl** объектов. Один **RDS. DataControl** объекта будет содержать SQL-запроса, запрашивает информацию о клиенте, второй будет содержать запрос, список товаров, приобретенных клиентом.  
  
-   В тегах ОБЪЕКТА каждого привязанного элемента управления укажите значение DATAFLD для задания значений для данных, которые нужно отобразить в каждого визуального элемента управления.  
  
 Не существует ограничения на количество число **RDS. DataControl** объекты, что можно объединить с помощью тегов ОБЪЕКТОВ, на одной веб-странице.  
  
 При определении **RDS. DataControl** на веб-странице, используйте ненулевое значение **высота** и **ширина** значения, например 1 (во избежание включения дополнительного пространства).  
  
 Компоненты клиента удаленной службы данных уже включены в состав Internet Explorer 4.0; Таким образом, необходимо включить параметр базу кода в ваш **RDS. DataControl** тега объекта.  
  
 Internet Explorer 4.0 или более поздней версии можно привязать к данным с помощью элементов управления HTML и элементов управления ActiveX® только в том случае, если они помечены как элементов управления модели подразделения.  
  
> [!NOTE]
>  **Microsoft Visual Basic пользователи** **RDS. DataControl** безопасный для сценариев и используется только в веб-приложения. Клиентское приложение Visual Basic имеет не требуется.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример объекта DataControl (VBScript)](../../../ado/reference/rds-api/datacontrol-object-example-vbscript.md)






















