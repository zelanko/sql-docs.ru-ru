---
title: Элемент Workload (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Workload element
ms.assetid: 68ffd473-6546-4015-98d0-3763165de65c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e81ea0aac9cfe7676abba18bc7dffb2e1561597b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62678722"
---
# <a name="workload-element-dta"></a>Элемент Workload (DTA)
  Позволяет задать рабочую нагрузку для использования в сеансе настройки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Требуется один раз для каждого элемента `DTAInput`.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Запуск и использование помощника по настройке ядра СУБД](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)|  
|**Дочерние элементы**|[Элемент File (DTA)](file-element-dta.md)<br /><br /> [Элемент Database для рабочей нагрузки (DTA)](database-element-for-workload-dta.md)<br /><br /> [Элемент EventString (DTA)](eventstring-element-dta.md)|  
  
## <a name="remarks"></a>Примечания  
 Рабочая нагрузка представляет собой набор инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] , выполняемый в одной или нескольких базах данных, которые необходимо настроить. Помощник по настройке ядра СУБД может использовать в качестве рабочей нагрузки скрипты [!INCLUDE[tsql](../../includes/tsql-md.md)] , файлы трассировки и таблицы трассировки.  
  
 Если заданы две рабочие нагрузки (одна во входном файле XML-данных, другая в командной строке с помощью средства **dta** ), для настройки будет использоваться последняя. Параметры настройки, заданные в командной строке, имеют приоритет над параметрами, заданными во входном XML-файле. Единственное исключение имеет место в том случае, когда пользовательская конфигурация вводится во входном XML-файле в режиме оценки. Например, если конфигурация вводится посредством элемента `Configuration` входного XML-файла и, кроме того, в качестве одного из параметров настройки задан элемент `EvaluateConfiguration`, параметры настройки из входного XML-файла получат приоритет над любыми параметрами настройки, введенными в командной строке.  
  
 Для каждого сеанса настройки должна быть указана одна рабочая нагрузка.  
  
## <a name="example"></a>Пример  
 В следующем примере кода задается **MyDatabase.MyDBOwner.TuningTable001** таблицу трассировки для `Workload` элемент. Таблица **TuningTable001** создана с помощью шаблона настройки в SQL Server Profiler путем сохранения выходной трассировки в виде таблицы.  
  
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
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
