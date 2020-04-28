---
title: Реализация полнотекстового поиска
ms.custom: seo-dt-2019
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- full-text search [SMO]
ms.assetid: 9ce9ad9c-f671-4760-90b5-e0c8ca051473
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 94605728f89483048ad35b3ec3247810bff70c57
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "74095185"
---
# <a name="implementing-full-text-search"></a>Реализация полнотекстового поиска
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Полнотекстовый поиск доступен для отдельных экземпляров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и представлен в SMO объектом <xref:Microsoft.SqlServer.Management.Smo.Server.FullTextService%2A>. <xref:Microsoft.SqlServer.Management.Smo.FullTextService> Объект находится в объекте **сервера** . Он используется для управления параметрами конфигурации службы [!INCLUDE[msCoName](../../../includes/msconame-md.md)] полнотекстового поиска. Объект <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalogCollection> принадлежит объекту <xref:Microsoft.SqlServer.Management.Smo.Database> и является коллекцией объектов <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog>, представляющих полнотекстовые каталоги, определенные в базе данных. Для каждой таблицы можно определить только один полнотекстовый индекс (в отличие от обычных индексов). Индекс представлен объектом <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> в объекте <xref:Microsoft.SqlServer.Management.Smo.Table>.  
  
 Чтобы создать службу полнотекстового поиска, необходимо иметь полнотекстовый каталог, определенный в базе данных, и индекс полнотекстового поиска, определенный на одной из таблиц в базе данных.  
  
 Сначала создайте полнотекстовый каталог для базы данных, вызвав конструктор <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> и указав имя каталога. Затем создайте полнотекстовый индекс, вызвав конструктор и указав таблицу, по которой он будет создан. Затем для полнотекстового индекса можно добавить столбцы индекса с помощью объекта <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn>, указав имя столбца в таблице. Потом укажите в свойстве <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.CatalogName%2A> путь к созданному каталогу. Наконец, вызовите метод <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.Create%2A> и создайте полнотекстовый индекс для экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Пример  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. [в статье Создание проекта Visual C&#35; SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-full-text-search-service-in-visual-basic"></a>Создание службы полнотекстового поиска на языке Visual Basic  
 В этом примере кода создается каталог полнотекстового поиска для таблицы `ProductCategory` в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]. Затем создается индекс полнотекстового поиска на столбце имен в таблице `ProductCategory`. Для индекса полнотекстового поиска необходимо, чтобы для столбца уже был определен уникальный индекс.  
  
```  
' compile with:   
' /r:Microsoft.SqlServer.SqlEnum.dll   
' /r:Microsoft.SqlServer.Smo.dll   
' /r:Microsoft.SqlServer.ConnectionInfo.dll   
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Sdk.Sfc  
Imports Microsoft.SqlServer.Management.Common  
  
Public Class A  
   Public Shared Sub Main()  
      ' Connect to the local, default instance of SQL Server.  
      Dim srv As Server = Nothing  
      srv = New Server()  
  
      ' Reference the AdventureWorks database.  
      Dim db As Database = Nothing  
      db = srv.Databases("AdventureWorks")  
  
      ' Reference the ProductCategory table.  
      Dim tb As Table = Nothing  
      tb = db.Tables("ProductCategory", "Production")  
  
      ' Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
      Dim ftc As FullTextCatalog = Nothing  
      ftc = New FullTextCatalog(db, "Test_Catalog")  
      ftc.IsDefault = True  
  
      ' Create the Full-Text Search catalog on the instance of SQL Server.  
      ftc.Create()  
  
      ' Define a FullTextIndex object varaible by supplying the parent table argument in the constructor.  
      Dim fti As FullTextIndex = Nothing  
      fti = New FullTextIndex(tb)  
  
      ' Define a FullTextIndexColumn object variable by supplying the parent index and column name arguments in the constructor.  
      Dim ftic As FullTextIndexColumn = Nothing  
      ftic = New FullTextIndexColumn(fti, "Name")  
  
      ' Add the indexed column to the index.  
      fti.IndexedColumns.Add(ftic)  
      fti.ChangeTracking = ChangeTracking.Automatic  
  
      ' Specify the unique index on the table that is required by the Full Text Search index.  
      fti.UniqueIndexName = "AK_ProductCategory_Name"  
  
      ' Specify the catalog associated with the index.  
      fti.CatalogName = "Test_Catalog"  
  
      ' Create the Full Text Search index on the instance of SQL Server.  
      fti.Create()  
   End Sub  
End Class  
```  
  
## <a name="creating-a-full-text-search-service-in-visual-c"></a>Создание службы полнотекстового поиска на языке Visual C#  
 В этом примере кода создается каталог полнотекстового поиска для таблицы `ProductCategory` в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]. Затем создается индекс полнотекстового поиска на столбце имен в таблице `ProductCategory`. Для индекса полнотекстового поиска необходимо, чтобы для столбца уже был определен уникальный индекс.  
  
```  
// compile with:   
// /r:Microsoft.SqlServer.SqlEnum.dll   
// /r:Microsoft.SqlServer.Smo.dll   
// /r:Microsoft.SqlServer.ConnectionInfo.dll   
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Sdk.Sfc;  
using Microsoft.SqlServer.Management.Common;  
  
public class A {  
   public static void Main() {  
      // Connect to the local, default instance of SQL Server.  
      Server srv = default(Server);  
      srv = new Server();  
  
      // Reference the AdventureWorks database.  
      Database db = default(Database);  
      db = srv.Databases ["AdventureWorks"];  
  
      // Reference the ProductCategory table.  
      Table tb = default(Table);  
      tb = db.Tables["ProductCategory", "Production"];  
  
      // Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
      FullTextCatalog ftc = default(FullTextCatalog);  
      ftc = new FullTextCatalog(db, "Test_Catalog");  
      ftc.IsDefault = true;  
  
      // Create the Full-Text Search catalog on the instance of SQL Server.  
      ftc.Create();  
  
      // Define a FullTextIndex object varaible by supplying the parent table argument in the constructor.  
      FullTextIndex fti = default(FullTextIndex);  
      fti = new FullTextIndex(tb);  
  
      // Define a FullTextIndexColumn object variable by supplying the parent index and column name arguments in the constructor.  
      FullTextIndexColumn ftic = default(FullTextIndexColumn);  
      ftic = new FullTextIndexColumn(fti, "Name");  
  
      // Add the indexed column to the index.  
      fti.IndexedColumns.Add(ftic);  
      fti.ChangeTracking = ChangeTracking.Automatic;  
  
      // Specify the unique index on the table that is required by the Full Text Search index.  
      fti.UniqueIndexName = "AK_ProductCategory_Name";  
  
      // Specify the catalog associated with the index.  
      fti.CatalogName = "Test_Catalog";  
  
      // Create the Full Text Search index on the instance of SQL Server.  
      fti.Create();  
   }  
}  
```  
  
## <a name="creating-a-full-text-search-service-in-powershell"></a>Создание службы полнотекстового поиска в PowerShell  
 В этом примере кода создается каталог полнотекстового поиска для таблицы `ProductCategory` в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]. Затем создается индекс полнотекстового поиска на столбце имен в таблице `ProductCategory`. Для индекса полнотекстового поиска необходимо, чтобы для столбца уже был определен уникальный индекс.  
  
```  
# Example of implementing a full text search on the default instance.  
# Set the path context to the local, default instance of SQL Server and database tables  
  
CD \sql\localhost\default\databases  
$db = get-item AdventureWorks2012  
  
CD AdventureWorks\tables  
  
#Get a reference to the table  
$tb = get-item Production.ProductCategory  
  
# Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
  
$ftc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextCatalog -argumentlist $db, "Test_Catalog2"  
$ftc.IsDefault = $true  
  
# Create the Full Text Search catalog on the instance of SQL Server.  
$ftc.Create()  
  
# Define a FullTextIndex object variable by supplying the parent table argument in the constructor.  
$fti = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndex -argumentlist $tb  
  
#  Define a FullTextIndexColumn object variable by supplying the parent index   
#  and column name arguments in the constructor.  
  
$ftic = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndexColumn -argumentlist $fti, "Name"  
  
# Add the indexed column to the index.  
$fti.IndexedColumns.Add($ftic)  
  
# Set change tracking  
$fti.ChangeTracking = [Microsoft.SqlServer.Management.SMO.ChangeTracking]::Automatic  
  
# Specify the unique index on the table that is required by the Full Text Search index.  
$fti.UniqueIndexName = "AK_ProductCategory_Name"  
  
# Specify the catalog associated with the index.  
$fti.CatalogName = "Test_Catalog2"  
  
# Create the Full Text Search Index  
$fti.Create()  
```  
  
  
