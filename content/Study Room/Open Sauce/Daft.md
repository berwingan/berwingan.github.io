---
title: Daft
draft: true
date: 2024-03-11
---
# Explode Index_Column
# Python Main
## daft/daft/init.pyi

1)
expr.list namespace
def explode(expr: PyExpr) -> PyExpr: ...

2)
class PyRecordBatch:
def explode(self, to_explode: list[PyExpr]) -> PyRecordBatch: ...

3)
class PyMicroPartition:
def explode(self, to_explode: list[PyExpr]) -> PyMicroPartition: ...  

4)
class LogicalPlanBuilder:
def explode(self, to_explode: list[PyExpr]) -> LogicalPlanBuilder: ...   -> daft/logical/builder.py


--------------------------
## daft/dataframe/dataframe.py
- def explode(self, *columns: ColumnInputType) -> "DataFrame": 
"DataFrame" class return -> forward references (same as from __future__ import annotations)
@DataframePublicAPI ---> decorator that expose function to public 
ColumnInputType = Union[Expression, str]
Expression -> ==daft.expressions==
### daft/exppressions/expressions.py


--------------------------
## daft/expressions/expressions.py

## daft/logical/builder.py
## daft/logical/map_partition_ops.py

## daft/execution/rust_physical_plan_shim.py

## daft/recordbatch/micropartition.py

## daft/recordbatch/recordbatch.py


----------------------------


# Rust