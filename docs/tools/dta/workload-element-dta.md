---
title: "Элемент Workload (DTA) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: Workload element
ms.assetid: 68ffd473-6546-4015-98d0-3763165de65c
caps.latest.revision: "16"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bc428a8f44fb2ca88a3aea2c93f9bdaf43b4e4f1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="workload-element-dta"></a>Элемент Workload (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Позволяет задать рабочую нагрузку для сеанса настройки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Требуется один раз для каждого элемента **DTAInput** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Запуск и использование помощника по настройке ядра СУБД](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)|  
|**Дочерние элементы**|[Элемент File (DTA)](../../tools/dta/file-element-dta.md)<br /><br /> [Элемент Database для рабочей нагрузки (DTA)](../../tools/dta/database-element-for-workload-dta.md)<br /><br /> [Элемент EventString (DTA)](../../tools/dta/eventstring-element-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 Рабочая нагрузка представляет собой набор инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] , выполняемый в одной или нескольких базах данных, которые необходимо настроить. Помощник по настройке ядра СУБД может использовать в качестве рабочей нагрузки скрипты [!INCLUDE[tsql](../../includes/tsql-md.md)] , файлы трассировки и таблицы трассировки.  
  
 Если заданы две рабочие нагрузки (одна во входном файле XML-данных, другая в командной строке с помощью средства **dta** ), для настройки будет использоваться последняя. Параметры настройки, заданные в командной строке, имеют приоритет над параметрами, заданными во входном XML-файле. Единственное исключение имеет место в том случае, когда пользовательская конфигурация вводится во входном XML-файле в режиме оценки. Например, если конфигурация вводится посредством элемента **Configuration** входного XML-файла и, кроме того, в качестве одного из параметров настройки задан элемент **EvaluateConfiguration** , параметры настройки из входного XML-файла получат приоритет над любыми параметрами настройки, введенными в командной строке.  
  
 Для каждого сеанса настройки должна быть указана одна рабочая нагрузка.  
  
## <a name="example"></a>Пример  
 В следующем примере кода задается таблица трассировки **MyDatabase.MyDBOwner.TuningTable001** для элемента **Workload** . Таблица **TuningTable001** создана с помощью шаблона настройки в SQL Server Profiler путем сохранения выходной трассировки в виде таблицы.  
  
```  
<DTAXML ...>  
  <DTAInput>  
    <Server>  
...code removed here...  
    </Server>  
    <Workload>  
      <Database>  
        <Name>MyDatabase</Name>  
        <Schema>  
          <Name>MyDBOwner</Name>  
            <Table>  
              <Name>TuningTable001</Name>  
            </Table>  
        </Schema>  
      </Database>  
    </Workload>  
...code removed here...  
  </DTAInput>  
</DTAXML>  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
