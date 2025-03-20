# ODDS-JUSTA
def calcular_odds_handicap(prob_vitoria, prob_empate, prob_derrota):
    """Calcula odds justas para diferentes Handicaps Asiáticos"""
    
    def calc_odd(prob):
        return round(1 / prob, 2) if prob > 0 else None

    odds = {}

    # HA 0.0 (DNB - Draw No Bet)
    prob_ha_0 = prob_vitoria / (1 - prob_empate)
    odds["HA 0.0"] = calc_odd(prob_ha_0)

    # HA -0.25 e HA +0.25
    prob_ha_neg_025 = prob_vitoria + (prob_empate / 2)
    prob_ha_pos_025 = prob_derrota + (prob_empate / 2)
    odds["HA -0.25"] = calc_odd(prob_ha_neg_025)
    odds["HA +0.25"] = calc_odd(prob_ha_pos_025)

    # HA -0.50 e HA +0.50
    prob_ha_neg_050 = prob_vitoria + prob_empate
    prob_ha_pos_050 = prob_derrota + prob_empate
    odds["HA -0.50"] = calc_odd(prob_ha_neg_050)
    odds["HA +0.50"] = calc_odd(prob_ha_pos_050)

    # HA -0.75 e HA +0.75
    prob_ha_neg_075 = prob_vitoria + (0.75 * prob_empate)
    prob_ha_pos_075 = prob_derrota + (0.75 * prob_empate)
    odds["HA -0.75"] = calc_odd(prob_ha_neg_075)
    odds["HA +0.75"] = calc_odd(prob_ha_pos_075)

    return odds

# Teste com valores
if __name__ == "__main__":
    prob_vitoria = 0.544  # 54.4%
    prob_empate = 0.303   # 30.3%
    prob_derrota = 0.152  # 15.2%

    odds_justas = calcular_odds_handicap(prob_vitoria, prob_empate, prob_derrota)

    # Exibir resultados
    for handicap, odd in odds_justas.items():
        print(f"{handicap}: {odd}")
