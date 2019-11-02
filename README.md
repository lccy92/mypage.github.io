＃mypage.github.io
//个人练习
//moveElement.js
function moveElement(elementId,final_x,final_y,interval) {
  if (!document.getElementById) return false;
  if (!document.getElementById(elementId)) return false;
  var elem = document.getElementById(elementId);
  var xpos = parseInt(elem.style.left);
  var ypos = parseInt(elem.style.top);
  if (xpos == final_x && ypos == final_y){
    return true;
  }
  if (xpos < final_x){
    xpos++;
  }
  if (xpos > final_x){
    xpos --;
  }
  if (ypos < final_y){
    ypos++;
  }
  if (ypos > final_y){
    ypos--;
  }
  elem.style.left = xpos + 'px';
  elem.style.top = ypos + ' px';
  var repeat = "moveElement('"+elementId+"',"+final_x+","+final_y+","+interval+")";
  movement = setTimeout(repeat,interval);
}

//positionMessage.js
function positionMessage() {
  if (!document.getElementById) return false;
  if (!document.getElementById('message')) return false;
  var elem = document.getElementById('message');
  elem.style.position = 'absolute';
  elem.style.left = '50px';
  elem.style.top = '100px';
  moveElement('message', 500,250,10);
  if (!document.getElementById('message2')) return false;
  var elem = document.getElementById('message2');
  elem.style.position = 'absolute';
  elem.style.left = '50px';
  elem.style.top = '50px';
  moveElement('message2', 125,125,20);

}
addLoadEvent(positionMessage);

//addLoadEvent.js
function addLoadEvent(func) {
  var oldonload = window.onload;
  if (typeof window.onload != 'function'){
    window.onload = func;
  }else{
    window.onload = function () {
      oldonload();
      func();
    }
  }
}
