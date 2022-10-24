# Custom SN Util switches and commands

## Custom Commands
```
{
    "fs": {
        "url": "sys_script_fix_list.do",
        "hint": "Open fix scripts",
        "fields": "",
        "order": 0,
        "overwriteurl": ""
    },
    "import": {
        "url": "https://hagerty$0.service-now.com/nav_to.do?uri=%2Fupload.do%3Fsysparm_referring_url%3Dsys_remote_update_set_list.do%253Fsysparm_fixed_query%253Dsys_class_name%253Dsys_remote_update_set%26sysparm_target%3Dsys_remote_update_set",
        "hint": "",
        "fields": "",
        "order": 0,
        "overwriteurl": ""
    },
    "spw": {
        "url": "sp_widget_list.do?sysparm_query=nameLIKE$0^ORDERBYDESCsys_updated_on",
        "hint": "Service Portal Widgets <search>",
        "fields": "name",
        "overwriteurl": "/sp_config?id=widget_editor&sys_id=$sysid",
        "inlineonly": true
    }
}
```  
- url: url to go to, or to search for when auto-completing the command
- hint: displayed in slash command UI
- fields: field(s - comma separated) displayed when auto-completing the command
- order: incdicates position in slash command UI dropdown when not filtered
- overwriteurl: once an auto-complete option is selected or the command is confirmed, overwrite the url value with this. You can pass in fields from selected auto-complete using $<field_name> if they were passed as part of the `fields` list. Use sysid instead of sys_id
- inlineonly: require a selection from auto-complete to confirm the command



## Custom Switches 
arnoudkooi.com/switch/

```
{
    "s": {
        "description": "Current Scope",
        "value": "^sys_scope=javascript:gs.getCurrentApplicationId()",
        "type": "encodedquerypart"
    },
    "p": {
        "description": "Filter Pinned",
        "value": "&sysparm_filter_pinned=true",
        "type": "querypart"
    },
    "t": {
        "description": "View Table Structure",
        "value": "sys_db_object.do?sys_id=$0&sysparm_refkey=name",
        "type": "link"
    },
    "pi": {
        "description": "Pop In - Open in full UI",
        "value": "/nav_to.do?uri=",
        "type": "prepend"
    }
}
```


### Types  
- `encodedquerypart` : Adds to the encoded query in the url of the current command
- `querypart` : Adds to the url query parameters of the current command  
- `link` : Overwrites the current command's url. May use the original command as a variable in the new url by using `$0` as shown above  
- `prepend` : Prepend the current command's url with value