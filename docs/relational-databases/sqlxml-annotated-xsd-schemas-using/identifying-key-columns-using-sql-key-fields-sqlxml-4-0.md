---
title: 使用 sql：索引鍵-欄位識別索引鍵資料行（SQLXML）
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nesting XML results
- proper nesting in results [SQLXML]
- sql:key-fields
- XSD schemas [SQLXML], key columns
- identifying key columns [SQLXML]
- annotated XSD schemas, key columns
- key columns [SQLXML]
- relationships [SQLXML], key columns
- hierarchical relationships [SQLXML]
- key-fields annotation
ms.assetid: 1a5ad868-8602-45c4-913d-6fbb837eebb0
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 71d42f9f3f819dc12964ea0f13de92dfc8db5663
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "75257395"
---
# <a name="identifying-key-columns-using-sqlkey-fields-sqlxml-40"></a>使用 sql:key-fields 來識別索引鍵資料行 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  針對 XSD 結構描述指定 XPath 查詢時，在大部分情況下都需要索引鍵資訊，才能在結果中取得正確的巢狀結構。 指定 [ **sql：索引鍵-欄位**] 注釋是確保產生適當階層的方式。  
  
> [!NOTE]  
>  若要確保適當的嵌套，建議您針對對應至資料表的專案指定**sql：索引鍵欄位**。 產生的 XML 會區分基礎結果集的排序。 如果未指定**sql：索引鍵-欄位**，則產生的 XML 格式可能不正確。  
  
 **Sql：索引鍵-欄位**的值會識別可唯一識別關聯中資料列的資料行。 如果需要多個資料行才能唯一識別某個資料列，這些資料行值就會以空格隔開。  
  
 當元素包含在元素和子專案之間定義的** \<sql： relationship>** ，但未提供在父元素中指定之資料表的主鍵時，您必須使用**sql：索引鍵欄位**注釋。  
  
## <a name="examples"></a>範例  
 若要使用下列範例建立工作範例，您必須符合某些需求。 如需詳細資訊，請參閱[執行 SQLXML 範例的需求](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md)。  
  
### <a name="a-producing-the-appropriate-nesting-when-sqlrelationship-does-not-provide-sufficient-information"></a>A. 當 sql： relationship> \<未提供足夠的資訊時，產生適當的嵌套  
 這個範例會顯示必須指定**sql：索引鍵-欄位**的位置。  
  
 請考慮下列結構描述。 架構會指定** \<order>** 和** \<customer>** 元素之間的階層，其中** \<order>** 元素是父系，而** \<customer>** 元素是子系。  
  
 Sql： relationship>標記是用來指定父子式關聯性。 ** \< ** 它會將 Sales.SalesOrderHeader 資料表中的 CustomerID 識別為參考 Sales.Customer 資料表中 CustomerID 子索引鍵的父索引鍵。 ** \<Sql： relationship>** 中提供的資訊並不足以唯一識別父資料表（SalesOrderHeader）中的資料列。 因此，如果沒有**sql：索引鍵-欄位**注釋，所產生的階層就不會正確。  
  
 使用** \<Order>** 上指定的**sql：索引鍵-欄位**，批註會唯一識別父系（SalesOrderHeader 資料表）中的資料列，而且其子項目會顯示在其父系之下。  
  
 這是結構描述：  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrdCust"  
        parent="Sales.SalesOrderHeader"  
        parent-key="CustomerID"  
        child="Sales.Customer"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"   
               sql:key-fields="SalesOrderID">  
   <xsd:complexType>  
     <xsd:sequence>  
     <xsd:element name="Customer" sql:relation="Sales.Customer"   
                       sql:relationship="OrdCust"  >  
       <xsd:complexType>  
         <xsd:attribute name="CustID" sql:field="CustomerID" />  
         <xsd:attribute name="SoldBy" sql:field="SalesPersonID" />  
       </xsd:complexType>  
     </xsd:element>  
     </xsd:sequence>  
     <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
     <xsd:attribute name= "CustomerID" type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a>若要建立這個結構描述的工作範例  
  
1.  複製上述的結構描述程式碼，並將其貼到文字檔中。 將檔案儲存為 KeyFields1.xml。  
  
2.  複製下列範本，並將其貼到文字檔中。 將檔案儲存為 KeyFields1T.xml，並放在儲存 KeyFields1.xml 的相同目錄中。 範本中的 XPath 查詢會傳回 CustomerID 小於3的** \<所有 Order>** 元素。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="KeyFields1.xml">  
            /Order[@CustomerID < 3]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     針對對應結構描述 (KeyFields1.xml) 指定的目錄路徑相對於儲存範本的目錄。 您也可以指定絕對路徑，例如：  
  
    ```  
    mapping-schema="C:\MyDir\KeyFields1.xml"  
    ```  
  
3.  建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。  

     如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 查詢](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。  
  
 這是部分結果集：  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
    <Order SalesOrderID="43860" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    <Order SalesOrderID="44501" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    <Order SalesOrderID="45283" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    .....  
</ROOT>  
```  
  
### <a name="b-specifying-sqlkey-fields-to-produce-proper-nesting-in-the-result"></a>B. 指定 sql:key-fields 在結果中產生適當的巢狀結構  
 在下列架構中，沒有使用** \<sql： relationship>** 所指定的階層。 架構仍然需要指定**sql： key-fields**注釋，以唯一識別 HumanResources Employee 資料表中的員工。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="HumanResources.Employee" sql:key-fields="EmployeeID" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Title">  
          <xsd:complexType>  
            <xsd:simpleContent>  
              <xsd:extension base="xsd:string">  
                 <xsd:attribute name="EmployeeID" type="xsd:integer" />  
              </xsd:extension>  
            </xsd:simpleContent>  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
   </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a>若要建立這個結構描述的工作範例  
  
1.  複製上述的結構描述程式碼，並將其貼到文字檔中。 將檔案儲存為 KeyFields2.xml。  
  
2.  複製下列範本，並將其貼到文字檔中。 將檔案儲存為 KeyFields2T.xml，並放在儲存 KeyFields2.xml 的相同目錄中。 範本中的 XPath 查詢會傳回所有** \<HumanResources>** 元素：  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="KeyFields2.xml">  
        /HumanResources.Employee  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     針對對應結構描述 (KeyFields2.xml) 指定的目錄路徑相對於儲存範本的目錄。 您也可以指定絕對路徑，例如：  
  
    ```  
    mapping-schema="C:\MyDir\KeyFields2.xml"  
    ```  
  
3.  建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。  
  
     如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 查詢](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。  
  
 以下是結果：  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <HumanResources.Employee>  
    <Title EmployeeID="1">Production Technician - WC60</Title>   
  </HumanResources.Employee>  
  <HumanResources.Employee>  
    <Title EmployeeID="2">Marketing Assistant</Title>   
  </HumanResources.Employee>  
  <HumanResources.Employee>  
    <Title EmployeeID="3">Engineering Manager</Title>   
  </HumanResources.Employee>  
  ...  
</ROOT>  
```  
  
  
