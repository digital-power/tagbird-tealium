# datahawk-tealium

Datahawk can visualise Tealium view and link calls when the code snippet below is deployed using a Tealium JavaScript Extension. The extension should be scoped to "All Tags - After Tags" and placed at the bottom of the list of extensions.

```javascript
/*
* Tealium JavaScript Extension: Datahawk Integration
* Enables visualisation of Tealium view/link calls by Datahawk (Google Chrome Plugin)
* This extension should be scoped to 'All tags - After tags' and placed at the bottom of the list of extensions
*/
var data = { version : utag.cfg.v, tags : [], load_rules : [], data_layer : b };
for(var tag in utag.loader.GV(utag.loader.cfg)){
    if(utag.loader.cfg[tag].load && utag.loader.cfg[tag].send){
      data.tags.push(tag);
    }
}
for(var rule in utag.cond){
    if(utag.cond[rule+""]) {
        data.load_rules.push(rule);
    }
}
window.tealium_event = window.tealium_event || [];
tealium_event.push(["event",a,data]);
```

