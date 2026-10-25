
/* /ai_website/static/src/public/ai_script_manager.js */
class AiScriptsManager{constructor(){this.observerEntries=new Set();}
runCallback(fn,args){return fn(...args);}
protectMutations(fn,scriptEl){return(...args)=>{try{this.flushObservers(false);return this.runCallback(fn,args,{scriptEl});}finally{this.flushObservers(true);}};}
whenReady(fn,scriptEl){const run=this.protectMutations(fn,scriptEl);if(document.readyState==="loading"){document.addEventListener("DOMContentLoaded",run,{once:true});}else{run();}}
flushObservers(aiChanges){for(const{observer,handleRecords}of this.observerEntries){const records=observer.takeRecords();if(records.length){handleRecords(records,aiChanges);}}}
trackElement(){}
registerCleanup(){}}
const manager=new AiScriptsManager();function getApi(scriptEl){return Object.freeze({protectMutations:(fn)=>manager.protectMutations(fn,scriptEl),trackElement:(element)=>manager.trackElement(element,scriptEl),registerCleanup:(cleanupFn)=>manager.registerCleanup(cleanupFn,scriptEl),whenReady:(fn)=>manager.whenReady(fn,scriptEl),});}
window.__aiScriptsManager__={getApi,manager};