# main.js

let currentTool = 'line';
let startX = null;
let startY = null;
let tempLine = null;

const svg = document.getElementById('canvas');

svg.addEventListener('mousedown', (e) => {
  if (currentTool === 'line') {
    startX = e.offsetX;
    startY = e.offsetY;

    tempLine = document.createElementNS("http://www.w3.org/2000/svg", "line");
    tempLine.setAttribute("x1", startX);
    tempLine.setAttribute("y1", startY);
    tempLine.setAttribute("x2", startX);
    tempLine.setAttribute("y2", startY);
    tempLine.setAttribute("stroke", "black");
    tempLine.setAttribute("stroke-width", "2");

    svg.appendChild(tempLine);
  }
});

svg.addEventListener('mousemove', (e) => {
  if (tempLine && currentTool === 'line') {
    tempLine.setAttribute("x2", e.offsetX);
    tempLine.setAttribute("y2", e.offsetY);
  }
});

svg.addEventListener('mouseup', () => {
  tempLine = null;
});

function setTool(tool) {
  currentTool = tool;
}
