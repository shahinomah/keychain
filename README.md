# keychain
Keychain STL maker using OpenSCAD

In the editor, please write (copy and paste) following code:

            // Custamizable Name Keychain
// ==========================================
// Customizable Name Keychain (Multi-Word Support)
// ==========================================

keychainText = "Shahino Mah";
fontStyle = "Arial:style=Bold";
fontSize = 14;
textHeight = 2;
backHeight = 3;
backPlateBorderSize = 2;
keychainHoleOffset = 1;
bridgeWidthMultiplier = 0.6; // <-- Easily adjust this if you change the name length

$fn = 40; // Smooth curves for circles and holes

// 1. Yellow Backplate with Keychain Loop & Word Bridge
color("gold")
linear_extrude(height = backHeight) {
    difference() {
        union() {
            // Text outline (automatically handles spaces and multiple words)
            offset(r = backPlateBorderSize)
                text(keychainText, size = fontSize, font = fontStyle, halign = "left", valign = "baseline");
            
            // Connecting bridge strip to join separated words into a single backplate
            translate([0, fontSize * 0.1])
                square([fontSize * len(keychainText) * bridgeWidthMultiplier, fontSize * 0.6], center = false);
            
            // Keychain ring tab attached to the left of the first letter
            translate([-backPlateBorderSize - 2 + keychainHoleOffset, fontSize * 0.35])
                circle(r = backPlateBorderSize + 2.5);
        }
        
        // Cut out the keychain hole
        translate([-backPlateBorderSize - 2 + keychainHoleOffset, fontSize * 0.35])
            circle(r = 2);
    }
}

// 2. Red Raised Text
color("red")
translate([0, 0, backHeight])
    linear_extrude(height = textHeight)
        text(keychainText, size = fontSize, font = fontStyle, halign = "left", valign = "baseline");

// Press Preview to see the design on the right. Press Render and wait for the design to be ready, before you can press STL to download the file

<img width="1440" height="792" alt="OpenSCAD-Project" src="https://github.com/user-attachments/assets/8aaa238e-df65-4f52-8247-bbb2097f51e3" />

// Or you can download the file, from this page (SCAD-Keychain-Custom.scad)
