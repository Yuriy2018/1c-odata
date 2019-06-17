# 1c-odata
1C v8 OData wrapper

```python
from odata1c.core import Infobase
from odata1c.postingmode import PostingMode
from datetime import datetime
from odata1c.document import Document
from odata1c.catalog import Catalog

connection = Infobase('http://myserver:port/','Infobase1','User','Password')

users = Catalog(connection,'Пользователи')
user.query() # get all
user.query(top=5)
user.query(top=5, skip=2)
user.query(select='Description, DeletionMark')
f="DeletionMark eq false" # Use singl quotes for strings!
user.query(odata_filter=f)

new = {'Description':'Новый пользователь','Комментарий':'hello odata'}

new_user = user.create(new)
edit_data = {'Комментарий':'hello odata edit'}
user.edit(guid=new_user['Ref_Key'], data=edit_data)
```
