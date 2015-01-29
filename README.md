Dynarec
=======

Parse transform that automaticaly generates and exports accessors for
all records declared within a module.

It generates and exports the following functions:

```erlang
get_value(field_name, Record) ->
    Record#record_name.field_name.

set_value(field_name, Value, Record = #record_name{}) ->
    Record#record_name{field_name = Value}.

records() ->
    [record_name1, record_name2, ...].

fields(record_name) ->
    [field_name1, field_name2, ...].

new_record(record_name) ->
    #record_name{}.
```

It runs at compile time using following preprocessor directive:

```erlang
-compile({parse_transform, dynarec}).
```

All those functions are added to the module that uses the
directive. Be aware that dynarec.erl must be compiled before any
module that uses it.
