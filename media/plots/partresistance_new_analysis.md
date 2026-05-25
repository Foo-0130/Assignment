# Descriptive Statistics for PartResistance (New Conditions)
mean_partresistance_new <- mean(filtered_data_new$PartResistance, na.rm = TRUE)
sd_partresistance_new <- sd(filtered_data_new$PartResistance, na.rm = TRUE)
cat(sprintf("Mean of PartResistance: %.4f\n", mean_partresistance_new))
cat(sprintf("Standard Deviation of PartResistance: %.4f\n", sd_partresistance_new))

# X-bar and R Control Charts for PartResistance (New Conditions)
# ... (rest of the control chart code for PartResistance, similar to previous cells) ...
# Define subgroup size
n_subgroup <- 5

# Prepare data for PartResistance
data_partresistance_new <- filtered_data_new$PartResistance
num_observations_pr_new <- length(data_partresistance_new)

# Ensure data length is a multiple of n_subgroup
data_for_subgroups_pr_new <- data_partresistance_new[1:(floor(num_observations_pr_new / n_subgroup) * n_subgroup)]
matrix_partresistance_new <- matrix(data_for_subgroups_pr_new, ncol = n_subgroup, byrow = TRUE)

# Create qcc objects for X-bar and R charts for PartResistance
qcc_xbar_pr_new <- qcc(matrix_partresistance_new, type = "xbar", plot = FALSE)
qcc_r_pr_new <- qcc(matrix_partresistance_new, type = "R", plot = FALSE)

# Extract limits for X-bar chart
cl_xbar_pr_new <- qcc_xbar_pr_new$center
ucl_xbar_pr_new <- qcc_xbar_pr_new$limits[1, 2]
lcl_xbar_pr_new <- qcc_xbar_pr_new$limits[1, 1]

# Extract limits for R chart
cl_r_pr_new <- qcc_r_pr_new$center
ucl_r_pr_new <- qcc_r_pr_new$limits[1, 2]
lcl_r_pr_new <- qcc_r_pr_new$limits[1, 1]

# Create data for plotting X-bar chart
plot_data_xbar_pr_new <- data.frame(
  Subgroup = 1:length(qcc_xbar_pr_new$statistics),
  Mean = qcc_xbar_pr_new$statistics
)

# Create data for plotting R chart
plot_data_r_pr_new <- data.frame(
  Subgroup = 1:length(qcc_r_pr_new$statistics),
  Range = qcc_r_pr_new$statistics
)

# Generate X-bar plot for PartResistance
p_xbar_pr_new <- ggplot(plot_data_xbar_pr_new, aes(x = Subgroup, y = Mean)) +
  geom_line(color = "#0072B2") +
  geom_point(color = "#0072B2") +
  geom_hline(yintercept = cl_xbar_pr_new, linetype = "solid", color = "#D55E00", size = 1) +
  geom_hline(yintercept = ucl_xbar_pr_new, linetype = "dashed", color = "#D55E00", size = 0.8) +
  geom_hline(yintercept = lcl_xbar_pr_new, linetype = "dashed", color = "#D55E00", size = 0.8) +
  labs(title = "X-bar Control Chart for PartResistance (New Conditions)",
       x = "Subgroup",
       y = "Subgroup Mean") +
  theme_minimal() +
  theme(plot.background = element_rect(fill = "white", color = NA),
        panel.background = element_rect(fill = "white", color = NA),
        axis.title.x = element_text(size = 18),
        axis.title.y = element_text(size = 18),
        axis.text.x = element_text(size = 14),
        axis.text.y = element_text(size = 14))

# Generate R plot for PartResistance
p_r_pr_new <- ggplot(plot_data_r_pr_new, aes(x = Subgroup, y = Range)) +
  geom_line(color = "#0072B2") +
  geom_point(color = "#0072B2") +
  geom_hline(yintercept = cl_r_pr_new, linetype = "solid", color = "#D55E00", size = 1) +
  geom_hline(yintercept = ucl_r_pr_new, linetype = "dashed", color = "#D55E00", size = 0.8) +
  geom_hline(yintercept = lcl_r_pr_new, linetype = "dashed", color = "#D55E00", size = 0.8) +
  labs(title = "R Control Chart for PartResistance (New Conditions)",
       x = "Subgroup",
       y = "Subgroup Range") +
  theme_minimal() +
  theme(plot.background = element_rect(fill = "white", color = NA),
        panel.background = element_rect(fill = "white", color = NA),
        axis.title.x = element_text(size = 18),
        axis.title.y = element_text(size = 18),
        axis.text.x = element_text(size = 14),
        axis.text.y = element_text(size = 14))

# Cp and Cpk Calculation for PartResistance (Assumed USL=7.5, LSL=6.5)
USL_pr <- 7.5
LSL_pr <- 6.5
Cp_pr <- (USL_pr - LSL_pr) / (6 * sd_partresistance_new)
Cpk_pr <- min((USL_pr - mean_partresistance_new) / (3 * sd_partresistance_new), (mean_partresistance_new - LSL_pr) / (3 * sd_partresistance_new))
cat(sprintf("Cp for PartResistance: %.4f\n", Cp_pr))
cat(sprintf("Cpk for PartResistance: %.4f\n", Cpk_pr))

