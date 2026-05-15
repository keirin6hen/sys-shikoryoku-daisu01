(function(){
  function updateOne(details){
    var s = details.querySelector('summary.hint__btn');
    if(!s) return;
    s.textContent = details.open ? '閉じる' : 'ヒント';
  }

  function init(){
    document.querySelectorAll('details.hint').forEach(updateOne);

    document.addEventListener('toggle', function(e){
      var d = e.target;
      if(d && d.matches && d.matches('details.hint')) updateOne(d);
    }, true);

    document.addEventListener('click', function(e){
      var s = e.target.closest && e.target.closest('summary.hint__btn');
      if(!s) return;
      var d = s.parentElement;
      setTimeout(function(){ updateOne(d); }, 0);
    }, true);
  }

  if(document.readyState === 'loading'){
    document.addEventListener('DOMContentLoaded', init);
  }else{
    init();
  }
})();