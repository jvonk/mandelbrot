//zoom by dragging cursor over area you wish to view.
//press <space> to go back to your previous view


var iterlimit = 50;
var EdgeSqr = 16;
var reload = 0;
// 640x200
var DispWidth = width;
var DispHeight = height;

// Z = a + j.b
var a = 0; // real part of Z
var b = 0; // imaginary part of Z

//var x1 = -0.633775964;  // left most real value
//var x2 = -0.633775960;   // right most real value
//var y1 = -0.4756460148;
//var y2 = -0.4756460144;
var pressx;
var pressy;
var releasex;
var releasey;
var x1 = -0.65;
var x2 = -0.63;
var y1 = -0.47;
var y2 = -0.49;
//var x1 = -1.5;
//var x2 =  1.5;
//var y1 = -2;
//var y2 =  1.5;
var oldx1s = [x1, 0];
var oldx2s = [x2, 0];
var oldy1s = [y1, 0];
var oldy2s = [y2, 0];
var b1 = x1, b2 = (x2-x1)/DispWidth;
var a1 = y1, a2 = (y2-y1)/DispHeight;
var p = 0;
var j = 0;
var greatestdraggx;
var greatestdraggy;

var mouseDragged = function() {
    noFill();
    strokeWeight(3);
    stroke(66, 34, 34);
    rect(pressx, pressy, -(pressx-mouseX), -(pressy-mouseY));
    fill(140, 140, 140, 50);
    rect(pressx, pressy, -(pressx-mouseX), -(pressy-mouseY));
};
var keyTyped = function() {
    x1 = oldx1s[reload];
    x2 = oldx2s[reload];
    y1 = oldy1s[reload];
    y2 = oldy2s[reload];
    //background(0, 0, 0);
        
    b1 = x1;
    b2 = (x2-x1)/DispWidth;
    a1 = y1;
    a2 = (y2-y1)/DispHeight;
    if (reload !== 0) {
        j = 0;
    }
    while (true) {
        if (keyIsPressed === false) {
            break;
        }
    }
    reload--; 
    
};
var mousePressed = function() {
    p = 1;
    pressx = mouseX;
    pressy = mouseY;
    
};
var mouseReleased = function() {
    if (p === 1) {
        reload++;
        releasex = mouseX;
        releasey = mouseY;
        noFill();
        strokeWeight(5);
        stroke(66, 34, 34);
        rect(pressx, pressy, -(pressx-releasex), -(pressy-releasey));
        oldx1s[reload] = x1;
        oldx2s[reload] = x2;
        oldy1s[reload] = y1;
        oldy2s[reload] = y2;
        var xa = x1;
        var xb = x2;
        var ya = y1;
        var yb = y2;
        x1 = map(pressx, 0, DispWidth, xa, xb);
        x2 = map(pressx-(pressx-releasex), 0, DispWidth, ya, yb);
        y1 = map(pressy, 0, DispHeight, xa, xb);
        y2 = map(pressy-(pressy-releasey), 0, DispHeight, ya, yb);
        background(0, 0, 0);
        
        b1 = x1;
        b2 = (x2-x1)/DispWidth;
        a1 = y1;
        a2 = (y2-y1)/DispHeight;
        j = 0;
    }
    
    p = 0;
};


var STEP = 1;

noStroke();


var plot = function(x, y) {
    rect(x, y, STEP, STEP);
};

//for (var j = 0; j < DispHeight; j += STEP) {
var draw = function() {
    
    a = a1 + a2*j;

    for (var i = 0; i < DispWidth; i += STEP) {
        b = b1 + b2*i;
        
        var x = a;
        var y = b;
        var xsqr = a*a;
        var ysqr = b*b;

        for (var k = 1; k <= iterlimit; k++) {
            var z = x;
            x = xsqr - ysqr + a;
            y = 2*y*z + b;
            xsqr = x*x;
            ysqr = y*y;

            if (xsqr + ysqr > EdgeSqr) {
                break;
            }
        }
            noStroke();
            fill(k/100*255-i/5,k/100*255-j/5,k/100*255-i/5);
            plot(i, j);
    }
    j+=STEP;
};


