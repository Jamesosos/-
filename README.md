# -
水火箭自由工程模擬器
default setting
寶特瓶總容量 (火箭大小): 1250 mL  min="500mL" max="2500mL" step="50mL" default value="1250mL" 
火箭自身淨重 (含尾翼噴嘴): 50 g  min="20 g" max="500 g" step="5 g" default value="50"
小蘇打粉 (粉末質量): 20 g min="0 g" max="300 g" step="1 g" default value="20 g" 
白醋量 (含有5%醋酸): 300 mL  min="0" max="2500" default value="300 mL" 

    // 5. 物理引擎計算 (PSI 壓力與懲罰)
    let pressurePsi = (gasProduced * 1000 / airSpace) * 14.7; 
    
    // 最佳推進介質比例 (30% 體積比最理想)
    let optimalRatio = 30;
    let ratioEfficiency = 1 - Math.abs(liquidRatio - optimalRatio) / 60;
    if (ratioEfficiency < 0) ratioEfficiency = 0;

    // 重量懲罰 (以 300g 為基礎死重)
    let weightPenalty = 500 / (500 + Math.max(0, totalWeight - 300));
    if (weightPenalty > 1.2) weightPenalty = 1.2;

    // 最終高度計算 (導入您前一個提及的公式)
    let baseScore = (pressurePsi * 2.2) * ratioEfficiency * weightPenalty;
    maxHeight = Math.max(0, baseScore);
