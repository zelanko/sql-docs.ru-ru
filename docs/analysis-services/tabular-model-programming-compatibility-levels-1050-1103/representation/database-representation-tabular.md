---
title: Базы данных (табличное) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1ca40737d9e37a97007f37ca79778b3c713b81a3
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/08/2018
---
# <a name="database-representationtabular"></a>Представление базы данных (табличное)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  В табличном режиме базы данных — это контейнер для всех объектов в табличной модели.  
  
## <a name="database-representation"></a>Представление базы данных  
 База данных — это место, где размещаются все объекты, образующие табличную модель. В базе данных разработчик находит такие объекты, как соединения, таблицы, роли и т. д.  
  
### <a name="database-in-amo"></a>База данных в объектах AMO  
 Если для управления табличным шаблоном базы данных табличной модели используются объекты AMO, то объект <xref:Microsoft.AnalysisServices.Database> из AMO соответствует логическому объекту базы данных в табличной модели по схеме «один к одному».  
  
> [!NOTE]  
>  Чтобы получить доступ к объекту базы данных, пользователь объектов AMO должен получить доступ к объекту сервера и установить с ним соединение.  
  
### <a name="database-in-adomdnet"></a>База данных в ADOMD.Net  
 Если ADOMD используется для просмотра табличного шаблона базы данных и отправки запросов к ней, то соединение с определенной базой данных устанавливается посредством объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 К определенной базе данных можно подключиться напрямую с помощью следующего фрагмента кода:  
  
```csharp  
using ADOMD = Microsoft.AnalysisServices.AdomdClient;  
…  
   ADOMD.AdomdConnection currrentCnx = new ADOMD.AdomdConnection("Data Source=<<server\instance>>;Catalog=<<database>>");  
   currrentCnx.Open();  
…  
  
```  
  
 Кроме того, через существующий объект соединения (если оно не закрыто) можно изменить текущую базу данных на другую, как показано в следующем фрагменте кода:  
  
```csharp  
currentCnx.ChangeDatabase("myOtherDatabase");  
  
```  
  
## <a name="database-in-amo"></a>База данных в объектах AMO  
 При использовании объектов AMO для управления объектом базы данных начните с объекта <xref:Microsoft.AnalysisServices.Server>. Затем найдите свою базу данных в коллекции баз данных или создайте новую базу данных, добавив ее в коллекцию.  
  
 В следующем фрагменте кода показаны действия по подключению к серверу и созданию пустой базы данных после того, как проверка показала, что она не существует.  
  
```  
  
AMO.Server CurrentServer = new AMO.Server();  
try  
{  
    CurrentServer.Connect(currentServerName);  
}  
catch (Exception cnxException)  
{  
    MessageBox.Show(string.Format("Error while trying to connect to server: [{0}]\nError message: {1}", currentServerName, cnxException.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    return;  
}  
newDatabaseName = DatabaseName.Text;  
if (CurrentServer.Databases.Contains(newDatabaseName))  
{  
    return;  
}  
try  
{  
    AMO.Database newDatabase = CurrentServer.Databases.Add(newDatabaseName);  
  
    CurrentServer.Update();  
}  
catch (Exception createDBxc)  
{  
    MessageBox.Show(String.Format("Database [{0}] couldn't be created.\n{1}", newDatabaseName, createDBxc.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    newDatabaseAvailable = false;  
}  
  
```  
  
 Чтобы получить практический опыт по использованию объектов AMO для создания и обработки представлений базы данных см. исходный код в образце Tabular AMO 2012; в частности, проверьте следующий исходный код: Database.cs. Этот образец доступен на сайте Codeplex. Образец кода приведен только для иллюстрации описываемых здесь логических концепций и не должен использоваться в рабочей среде.  
  
  
