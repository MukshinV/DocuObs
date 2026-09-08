Use client diff patches (via **NEMO** - Ragexe Patcher): Under the `Feature` tab, check **Enable Custom Camera Zoom** and **Remove Max Camera Limit** to bypass the 14-cell default restriction

To change how far mobs and other players appear on your screen and when they engage you:
- Navigate to your server directory and open the configuration file: `~/conf/battle/monster.conf`.
- Locate the `view_range_rate` and `chase_range_rate` settings. These adjust how far mobs can see you (based on their internal `mob_db` range settings).

Character.conf
// Visible area size (how many squares away from a player they can see)
area_size: 17