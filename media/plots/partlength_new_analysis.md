# Descriptive Statistics for PartLength (New Conditions)
mean_partlength_new <- mean(filtered_data_new$PartLength, na.rm = TRUE)
sd_partlength_new <- sd(filtered_data_new$PartLength, na.rm = TRUE)
cat(sprintf("Mean of PartLength: %.4f\n", mean_partlength_new))
cat(sprintf("Standard Deviation of PartLength: %.4f\n", sd_partlength_new))

# X-bar and R Control Charts for PartLength (New Conditions)
# ... (rest of the control chart code for PartLength, similar to previous cells) ...
# Define subgroup size
n_subgroup <- 5

# Prepare data for PartLength
data_partlength_new <- filtered_data_new$PartLength
num_observations_pl_new <- length(data_partlength_new)

# Ensure data length is a multiple of n_subgroup
data_for_subgroups_pl_new <- data_partlength_new[1:(floor(num_observations_pl_new / n_subgroup) * n_subgroup)]
matrix_partlength_new <- matrix(data_for_subgroups_pl_new, ncol = n_subgroup, byrow = TRUE)

# Create qcc objects for X-bar and R charts for PartLength
qcc_xbar_pl_new <- qcc(matrix_partlength_new, type = "xbar", plot = FALSE)
qcc_r_pl_new <- qcc(matrix_partlength_new, type = "R", plot = FALSE)

# Extract limits for X-bar chart
cl_xbar_pl_new <- qcc_xbar_pl_new$center
ucl_xbar_pl_new <- qcc_xbar_pl_new$limits[1, 2]
lcl_xbar_pl_new <- qcc_xbar_pl_new$limits[1, 1]

# Extract limits for R chart
cl_r_pl_new <- qcc_r_pl_new$center
ucl_r_pl_new <- qcc_r_pl_new$limits[1, 2]
lcl_r_pl_new <- qcc_r_pl_new$limits[1, 1]

# Create data for plotting X-bar chart
plot_data_xbar_pl_new <- data.frame(
  Subgroup = 1:length(qcc_xbar_pl_new$statistics),
  Mean = qcc_xbar_pl_new$statistics
)

# Create data for plotting R chart
plot_data_r_pl_new <- data.frame(
  Subgroup = 1:length(qcc_r_pl_new$statistics),
  Range = qcc_r_pl_new$statistics
)

# Generate X-bar plot for PartLength
p_xbar_pl_new <- ggplot(plot_data_xbar_pl_new, aes(x = Subgroup, y = Mean)) +
  geom_line(color = "#0072B2") +
  geom_point(color = "#0072B2") +
  geom_hline(yintercept = cl_xbar_pl_new, linetype = "solid", color = "#D55E00", size = 1) +
  geom_hline(yintercept = ucl_xbar_pl_new, linetype = "dashed", color = "#D55E00", size = 0.8) +
  geom_hline(yintercept = lcl_xbar_pl_new, linetype = "dashed", color = "#D55E00", size = 0.8) +
  labs(title = "X-bar Control Chart for PartLength (New Conditions)",
       x = "Subgroup",
       y = "Subgroup Mean") +
  theme_minimal() +
  theme(plot.background = element_rect(fill = "white", color = NA),
        panel.background = element_rect(fill = "white", color = NA),
        axis.title.x = element_text(size = 18),
        axis.title.y = element_text(size = 18),
        axis.text.x = element_text(size = 14),
        axis.text.y = element_text(size = 14))

# Generate R plot for PartLength
p_r_pl_new <- ggplot(plot_data_r_pl_new, aes(x = Subgroup, y = Range)) +
  geom_line(color = "#0072B2") +
  geom_point(color = "#0072B2") +
  geom_hline(yintercept = cl_r_pl_new, linetype = "solid", color = "#D55E00", size = 1) +
  geom_hline(yintercept = ucl_r_pl_new, linetype = "dashed", color = "#D55E00", size = 0.8) +
  geom_hline(yintercept = lcl_r_pl_new, linetype = "dashed", color = "#D55E00", size = 0.8) +
  labs(title = "R Control Chart for PartLength (New Conditions)",
       x = "Subgroup",
       y = "Subgroup Range") +
  theme_minimal() +
  theme(plot.background = element_rect(fill = "white", color = NA),
        panel.background = element_rect(fill = "white", color = NA),
        axis.title.x = element_text(size = 18),
        axis.title.y = element_text(size = 18),
        axis.text.x = element_text(size = 14),
        axis.text.y = element_text(size = 14))

# Cp and Cpk Calculation for PartLength (Assumed USL=52, LSL=48)
USL_pl <- 52
LSL_pl <- 48
Cp_pl <- (USL_pl - LSL_pl) / (6 * sd_partlength_new)
Cpk_pl <- min((USL_pl - mean_partlength_new) / (3 * sd_partlength_new), (mean_partlength_new - LSL_pl) / (3 * sd_partlength_new))
cat(sprintf("Cp for PartLength: %.4f\n", Cp_pl))
cat(sprintf("Cpk for PartLength: %.4f\n", Cpk_pl))

