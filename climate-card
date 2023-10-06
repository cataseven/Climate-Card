class ClimateCard extends HTMLElement {
    set hass(hass) {
      if (!this.content) {
        const card = document.createElement('ha-card');
        card.header = 'Climate Control';
        this.content = document.createElement('div');
        this.content.style.padding = '16px';
        card.appendChild(this.content);
        this.appendChild(card);
      }
  
      const entityId = this.config.entity;
      const entity = hass.states[entityId];
  
      if (entity) {
        const currentTemperature = entity.attributes.current_temperature;
        const targetTemperature = entity.attributes.temperature;
        const mode = entity.attributes.operation_mode;
  
        this.content.innerHTML = `
          <h2>${entity.attributes.friendly_name}</h2>
          <p>Current Temperature: ${currentTemperature}°C</p>
          <p>Target Temperature: ${targetTemperature}°C</p>
          <p>Mode: ${mode}</p>
        `;
      } else {
        this.content.innerHTML = 'Entity not found';
      }
    }
  
    setConfig(config) {
      if (!config.entity) {
        throw new Error('You need to specify an entity');
      }
      this.config = config;
    }
  }
  
  customElements.define('custom-climate-card', CustomClimateCard);
